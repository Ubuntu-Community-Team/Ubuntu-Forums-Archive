---
title: "utorrent installation help!"
date: 2011-12-26
forum: Installation &amp; Upgrades
---

### Post by maccollie on 2011-12-26
I downloaded the linux package from utorrent.com
I extracted to downloads folder, then I ran the utserver exe from terminal:

tom@ubuntu:~$ cd Downloads/utorrent-server-v3_0/
tom@ubuntu:~/Downloads/utorrent-server-v3_0$ sudo ./utserver
[sudo] password for tom: 
server started - using locale en_US.UTF-8
Using locale en_US.UTF-8
total physical memory -1 max disk cache 33554432
File not found during integrity check: ./dht.dat
File not found during integrity check: ./dht.dat.new
File not found during integrity check: ./dht.dat.old
File not found during integrity check: ./rss.dat
File not found during integrity check: ./rss.dat.new
File not found during integrity check: ./rss.dat.old
Loaded ipfilter.dat (0 entries)
File not found during integrity check: ./resume.dat
File not found during integrity check: ./resume.dat.new
File not found during integrity check: ./resume.dat.old
IPv6 is installed

?? any idea what I should do next?
If you can, tell me algorithmic instructions because I'm very new to using linux

thanks!

---

### Post by darkod on 2011-12-26
If you are new to linux I suggest using the Transmission client, it comes with Ubuntu. It has a GUI and it's easier to run and configure compared to utorrent it seems.

The utorrent manual also says a GUI exists, but there are no details if you need to configure it first and how, and I'm not familiar with it.

---

### Post by maccollie on 2011-12-26
I guess I'll have to.

I prefer utorrent because I'm familiar with its settings.
I don't know how to deny legacy collections or force protocol encryption in the transmission client 
also my tracker filter only works in utorrent

---

### Post by Jay Car on 2011-12-26
> **maccollie said:**
> I guess I'll have to.

I prefer utorrent because I'm familiar with its settings.
I don't know how to deny legacy collections or force protocol encryption in the transmission client 
also my tracker filter only works in utorrent

Try qbittorrent. Search for it in Synaptic.  It's very nice, easy to use, you can force encryption - and adjust a variety of other settings if you want - it even has a search option available.

I've tried so many different torrent programs that I nearly gave up looking for something stable and easy to use, that also gives options to change important settings, if needed. Qbittorrent fit that sescription for me. 

You might like it too!  :)

---

### Post by Rubi1200 on 2011-12-26
I'd second what Jay Car suggested and give qbittorrent a spin around the block; works very nicely for me too.

---

### Post by papibe on 2011-12-26
Check post #10 in this [thread]("http://ubuntuforums.org/showthread.php?t=1842045&highlight=utserver"). The utserver GUI is web based.

Regards.

BTW, **do not** run utserver using sudo.

---

### Post by raja.genupula on 2011-12-27
+1

I support Fatrat also for torrent download .

---

