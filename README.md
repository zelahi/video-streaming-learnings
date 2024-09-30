# Server-side Ad Insertion

## Nginx Setup

Install nginx, On mac:

```
brew install nginx
```

Modifications I made were:
    1. First I added the mime types based on the instructions here: https://developer.apple.com/documentation/http-live-streaming/deploying-a-basic-http-live-streaming-hls-stream

    2. After that, restart Nginx with the correct config
        ```
        nginx -c /Users/zuhayrelahi/Projects/ads-insertion-service/config/nginx.conf   
        ```
    
    **Note** If nginx is currently running then we need to stop it and restart it`

## Verifying and Testing HLS Stream

1. First I installed ffmpeg: 
```
brew install ffmpeg
```

2. Convert the mp4 file
```
ffmpeg -i mp4-files/file_example_MP4_640_3MG.mp4 -codec: copy -start_number 0 -hls_time 10 -hls_list_size 0 -f hls hls-files/example.m3u8
```

3. I updated my Nginx configuration to service the .m3u8 and .ts files

4. After downloading VLC, I tested the app