---
title: "Apache2 with mod_musicindex sends empty m3u"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by sambitbasu on 2008-05-12
I ran mod_musicindex (without icecast) to stream music from 7.04 (Feisty Fawn). It worked great.

I upgraded to 7.10 (Gutsy Gibbon) last week [yes, I deliberately run (current release -1)]. But now mod-musicindex has stopped streaming. I have  the configuration. It sends the plyalist.m3u file, but without any file information.

The request:

GET /media/media_hdd/media/audio/mp3/acd/Various/mymusic.mp3?stream HTTP/1.1
Host: myserver:8000
User-Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.14) Gecko/20080404 Firefox/2.0.0.14
Accept: text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Connection: keep-alive
-----------------------
The response:

HTTP/1.1 200 OK
Date: Mon, 12 May 2008 22:48:45 GMT
Server: Apache/2.2.4 (Ubuntu) mod_musicindex/1.2.0
Content-Disposition: filename = "playlist.m3u"
Content-Length: 8
Keep-Alive: timeout=15, max=100
Connection: Keep-Alive
Content-Type: audio/x-mpegurl

#EXTM3U
-----------------------

Any idea, what's wrong? And more importantly, how to fix it?


Thanks.

---

