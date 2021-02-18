# Readme    

Simple Spring Boot application showing HTTP2 config
 
## Step1 Simple WebApp
  
    curl -sI http://127.0.0.1:8080
    HTTP/1.1 200 
    Content-Type: text/plain;charset=UTF-8
    Content-Length: 7
    Date: Thu, 18 Feb 2021 10:44:59 GMT
    
## Step2 Enable HTTP2 (HTTP/2 only works over HTTPS)

    curl -k -sI https://127.0.0.1:8443
    HTTP/2 200 
    content-type: text/plain;charset=UTF-8
    content-length: 7
    date: Thu, 18 Feb 2021 11:24:42 GMT
    
## Step3 Configure Spring Security to require HTTPS requests

    > curl -vsI http://127.0.0.1:8080
    *   Trying 127.0.0.1...
    * TCP_NODELAY set
    * Connection failed
    * connect to 127.0.0.1 port 8080 failed: Connection refused
    * Failed to connect to 127.0.0.1 port 8080: Connection refused
    * Closing connection 0

## Step3 Redirect HTTP -> HTTPS

    > curl -sI http://127.0.0.1:8080    
    HTTP/1.1 302 
    Cache-Control: private
    Expires: Thu, 01 Jan 1970 00:00:00 GMT
    Location: https://127.0.0.1:8443/
    Transfer-Encoding: chunked
    Date: Thu, 18 Feb 2021 22:38:59 GMT

