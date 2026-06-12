---
title: "Installation on Acer E3-111-C6LG Laptop"
date: 2014-10-19
forum: Installation &amp; Upgrades
---

### Post by lena.marie.bruckne on 2014-10-19
Hey guys,
I recently bought an Acer E3-111-C6LG laptop. However, I'm absolutel not happy with it. After a lot of pain, I managed to install Ubuntu 12.04.5. Everything seems working fine so far however, whenever I try to play mp3s with mplayer for example it is lagging so badly that I just turn it off. Same with youtube videos that I try watch in the browser - forget it. On the other hand I can watch movies that I downloaded before. Did I mess something up with the installation or is it not using the appropriate drivers because I can run VirtualBox with a Win7 guest system without noticeable delays in the workflow. Does anybody have the same problems?

---

### Post by ibjsb4 on 2014-10-20
> or is it not using the appropriate driver
Looks like there is a restricted driver.

[https://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProdId=3523](https://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProdId=3523)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=install+restricted+driver&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=install+restricted+driver&sa=Search&cof=FORID:9)

---

### Post by lena.marie.bruckne on 2014-10-20
Hi, but I'm not sure whether installing a video driver really solves my problem. Because why does this happen with ordinary mp3 files? It's just music, no video. And why does it work with movies in avi format that are on my hd but youtube videos in the browser cause problems?

---

### Post by ibjsb4 on 2014-10-20
Do you have ubuntu-restricted-extras installed?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Its in the software center.

---

### Post by lena.marie.bruckne on 2014-10-20
No it wasn't installed before. I did it now, but no change. Tried an mp3 music file, still lagging.

---

### Post by ibjsb4 on 2014-10-21
Try monitoring your memory/cpu usage wile playing something.  In terminal:
```
top
```

---

### Post by lena.marie.bruckne on 2014-10-21
Alright I did that but I don't see anything abnormal. %CPU is like 5 for  mplayer and 8 for pulseaudio. %MEM is below 0.3 for both. I tried  playing around with the nice-level but didn't change anything.

---

### Post by ibjsb4 on 2014-10-21
Not even xorg ??
Ok, thats a dead end.

Try a different media player like vlc or maybe mplayer.

---

### Post by lena.marie.bruckne on 2014-10-22
Well, I mean of course, xorg is running but cpu time consumption and mem are normal I would say. It's not like it eats up all my resources. Here are a couple of screenshots I made while playing the mp3 file. And I don't think it's a matter of which player I use, because it doesn't work with any of them. I usually use mplayer from in the command line, but I of course also tried vlc before, but same effect.

---

### Post by ibjsb4 on 2014-10-22
I mention xorg because I had still hope it would be a driver problem, but its not eating up your cpu.

I'm out of ideas.

---

### Post by lena.marie.bruckne on 2014-10-26
Hi,
I already asked a similar question in the Installation forum however the answer wasn't really helpful so I try it here from a different angle. Recently, I bought a new Acer E3-111-C6LG laptop. I have a Intel Celeron quad Core N2930 processor, 4GB Ram, 500 GB harddisk. After some time I managed to install ubuntu 12.04 on it. Everything seems to work fine, however, I cannot play mp3 files or watch a youtube video in the browser because they always lag, badly! In general, the computer works fine you know, no problems. I use VirtualBox and run a Win7 in it, and so on, no problems at all. I changed the the swappiness level, since hard disk access is expensive and I have plenty of RAM. But still, can't listen to music. The guys from the Installation forum thought it might be a driver problem, but I don't see anything weird going on when I monitor it with top. No graphic issues whatsoever. So could it be that my processor is just too damn slow? Does anyone of you has experience with it? It would be really pathetic to be honest if that's the case.

---

### Post by QIII on 2014-10-26
Threads merged.

Please do no start threads on the same subject in different areas of the forum.  This leads to duplication of effort by the community and can be confusing.

Rather than starting a new thread either:

1.  Use the report button and ask the staff to move the thread.  If we believe you would have better luck somewhere else, we will do this.  Otherwise, we will leave it where it is.

2.  Add a new post to the thread with the word "Bump".  This will push the thread back up to the top of the stack and get it visible again.

Thanks.

---

### Post by lena.marie.bruckne on 2014-10-27
So could it be that my processor is just too damn slow? Does anyone of you has experience with it?

---

