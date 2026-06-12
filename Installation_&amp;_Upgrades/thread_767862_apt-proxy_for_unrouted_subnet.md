---
title: "apt-proxy for unrouted subnet"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by hessml on 2008-04-25
I'm trying to get apt-proxy setup. This is where I'm at: 

- 8.04 Server AMD 64 
- Server on 2 networks: 1 public, 1 private; the private one is not routed
- I modified /etc/apt-proxy/apt-proxy-v2.conf as follows: 
* uncommented the address line and set to private subnet address = 10.0.2.254 
* Change [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) to [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) 
- I edited /etc/apt/sources.list and replaced all the server addresses with "10.0.2.254:9999" 
- I start the server with sudo /etc/init.d/apt-proxy restart 
- It starts to do some stuff and then stops: 

Get:2 [http://10.0.2.254](http://10.0.2.254) hardy-updates Release.gpg [191B] 
Ign [http://10.0.2.254](http://10.0.2.254) hardy-updates/main Translation-en_US 
Ign [http://10.0.2.254](http://10.0.2.254) hardy-updates/restricted Translation-en_US 
Get:3 [http://10.0.2.254](http://10.0.2.254) hardy-security Release.gpg [191B] 
Ign [http://10.0.2.254](http://10.0.2.254) hardy-security/main Translation-en_US 
Ign [http://10.0.2.254](http://10.0.2.254) hardy-security/restricted Translation-en_US 
Ign [http://10.0.2.254](http://10.0.2.254) hardy-security/universe Translation-en_US 
Ign [http://10.0.2.254](http://10.0.2.254) hardy-security/multiverse Translation-en_US 
Ign [http://10.0.2.254](http://10.0.2.254) hardy Release 
Ign [http://10.0.2.254](http://10.0.2.254) hardy-updates Release 
Ign [http://10.0.2.254](http://10.0.2.254) hardy-security Release 
Ign [http://10.0.2.254](http://10.0.2.254) hardy/main Packages 
Ign [http://10.0.2.254](http://10.0.2.254) hardy/restricted Packages 
97% [Waiting for headers] 

Doing a netstat -nta 
Active Internet connections (servers and established) 
Proto Recv-Q Send-Q Local Address Foreign Address State 
tcp 0 0 10.0.2.254:9999 0.0.0.0:* LISTEN 
tcp 0 0 10.0.2.254:46769 10.0.2.254:9999 ESTABLISHED 
tcp 0 0 10.0.2.254:9999 10.0.2.254:46769 ESTABLISHED 
tcp6 0 0 :::22 :::* LISTEN 
tcp6 0 0 xx.xx.xx.67:22 xx.xx.xx.69:39835 ESTABLISHED 
tcp6 0 0 xx.xx.xx.67:22 xx.xx.xx.69:40624 ESTABLISHED 
tcp6 0 0 xx.xx.xx.67:22 xx.xx.xx.69:40672 ESTABLISHED 

There doesn't appear to be any outbound connections trying to download anything. 

Tailing the log gives this: 

2008/04/25 16:03 -0700 [Channel,5,10.0.2.254] [debug] Header: Host: 10.0.2.254:9999 
2008/04/25 16:03 -0700 [Channel,5,10.0.2.254] [debug] Header: Connection: keep-alive 
2008/04/25 16:03 -0700 [Channel,5,10.0.2.254] [debug] Header: User-Agent: Ubuntu APT-HTTP/1.3 (0.7.9ubuntu16) 
2008/04/25 16:03 -0700 [Channel,5,10.0.2.254] [debug] Headers: Host: 10.0.2.254:9999, Connection: keep-alive, User-Agent: Ubuntu APT-HTTP/1.3 (0.7.9ubuntu16)
2008/04/25 16:03 -0700 [Channel,5,10.0.2.254] [HttpRequestClient] Processing request for: /ubuntu/dists/hardy/main/source/Sources.bz2 
2008/04/25 16:03 -0700 [Channel,5,10.0.2.254] [HttpRequestClient] Request: GET /ubuntu/dists/hardy/main/source/Sources.bz2 backend=ubuntu uri=/ubuntu/dists/hardy/main/source/Sources.bz2 
2008/04/25 16:03 -0700 [Channel,5,10.0.2.254] [HttpRequestClient] backend: ubuntu [<apt_proxy.apt_proxy.BackendServer instance at 0xfb9ef0>] 
2008/04/25 16:03 -0700 [Channel,5,10.0.2.254] [debug] New Cache entry: dists/hardy/main/source/Sources.bz2 
2008/04/25 16:03 -0700 [Channel,5,10.0.2.254] [CacheEntry] Add request: <GET /ubuntu/dists/hardy/main/source/Sources.bz2 HTTP/1.1> total clients: 1 state:New 
2008/04/25 16:03 -0700 [Channel,5,10.0.2.254] [CacheEntry] this is a real request:/var/cache/apt-proxy/ubuntu/dists/hardy/main/source/Sources.bz2 
2008/04/25 16:03 -0700 [Channel,5,10.0.2.254] [CacheEntry] start download:dists/hardy/main/source/Sources.bz2 
2008/04/25 16:03 -0700 [Channel,5,10.0.2.254] [DownloadQueue] queue file ubuntu/dists/hardy/main/source/Sources.bz2 
2008/04/25 16:05 -0700 [Channel,5,10.0.2.254] [Channel] Client connection closed 
2008/04/25 16:05 -0700 [Channel,5,10.0.2.254] [HttpRequestClient] connectionLost 
2008/04/25 16:05 -0700 [Channel,5,10.0.2.254] Top 10: 
2008/04/25 16:05 -0700 [Channel,5,10.0.2.254] 253 WeakKeyDictionary 
2008/04/25 16:05 -0700 [Channel,5,10.0.2.254] 35 Ephemeral 
2008/04/25 16:05 -0700 [Channel,5,10.0.2.254] 28 Logger 
2008/04/25 16:05 -0700 [Channel,5,10.0.2.254] 24 Protocol 
2008/04/25 16:05 -0700 [Channel,5,10.0.2.254] 21 HttpRequestClient 
2008/04/25 16:05 -0700 [Channel,5,10.0.2.254] 19 FileType 
2008/04/25 16:05 -0700 [Channel,5,10.0.2.254] 17 CacheEntry 
2008/04/25 16:05 -0700 [Channel,5,10.0.2.254] 16 _SocketCloser 
2008/04/25 16:05 -0700 [Channel,5,10.0.2.254] 14 Resource 
2008/04/25 16:05 -0700 [Channel,5,10.0.2.254] 13 HttpFetcher 
2008/04/25 16:05 -0700 [-] [CacheEntry] Last request removed for /var/cache/apt-proxy/ubuntu/dists/hardy/main/source/Sources.bz2 
2008/04/25 16:05 -0700 [-] [Backend] entry_done: dists/hardy/main/source/Sources.bz2 
2008/04/25 16:05 -0700 [Channel,6,10.0.2.254] [HttpRequestClient] New Request, queued=0 
2008/04/25 16:05 -0700 [Channel,6,10.0.2.254] [debug] Header: Host: 10.0.2.254:9999 
2008/04/25 16:05 -0700 [Channel,6,10.0.2.254] [debug] Header: Connection: keep-alive 
2008/04/25 16:05 -0700 [Channel,6,10.0.2.254] [debug] Header: User-Agent: Ubuntu APT-HTTP/1.3 (0.7.9ubuntu16) 
2008/04/25 16:05 -0700 [Channel,6,10.0.2.254] [debug] Headers: Host: 10.0.2.254:9999, Connection: keep-alive, User-Agent: Ubuntu APT-HTTP/1.3 (0.7.9ubuntu16)
2008/04/25 16:05 -0700 [Channel,6,10.0.2.254] [HttpRequestClient] Processing request for: /ubuntu/dists/hardy/restricted/source/Sources.bz2 
2008/04/25 16:05 -0700 [Channel,6,10.0.2.254] [HttpRequestClient] Request: GET /ubuntu/dists/hardy/restricted/source/Sources.bz2 backend=ubuntu uri=/ubuntu/dists/hardy/restricted/source/Sources.bz2 
2008/04/25 16:05 -0700 [Channel,6,10.0.2.254] [HttpRequestClient] backend: ubuntu [<apt_proxy.apt_proxy.BackendServer instance at 0xfb9ef0>] 
2008/04/25 16:05 -0700 [Channel,6,10.0.2.254] [debug] New Cache entry: dists/hardy/restricted/source/Sources.bz2 
2008/04/25 16:05 -0700 [Channel,6,10.0.2.254] [CacheEntry] Add request: <GET /ubuntu/dists/hardy/restricted/source/Sources.bz2 HTTP/1.1> total clients: 1 state:New 
2008/04/25 16:05 -0700 [Channel,6,10.0.2.254] [CacheEntry] this is a real request:/var/cache/apt-proxy/ubuntu/dists/hardy/restricted/source/Sources.bz2 
2008/04/25 16:05 -0700 [Channel,6,10.0.2.254] [CacheEntry] start download:dists/hardy/restricted/source/Sources.bz2 
2008/04/25 16:05 -0700 [Channel,6,10.0.2.254] [DownloadQueue] queue file ubuntu/dists/hardy/restricted/source/Sources.bz2 

From the log it appears that it is trying to using the listening address to connect to the outside world which isn't going to work because it is unrouted subnet. Any idea on how I can get around this? Or am I completely off base and is it something else?

---

