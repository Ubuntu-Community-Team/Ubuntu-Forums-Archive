---
title: "chrome4 can't play html5 videos"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by suoko on 2009-10-26
do i have to use chrome ?
or continue with ff ?

---

### Post by kahping on 2009-10-26
you don't *have* to use chrome. why not stick with ff?

---

### Post by Joe_Bishop on 2009-10-26
> **suoko said:**
> do i have to use chrome ?
or continue with ff ?
sudo aptitude install chromium-codecs-ffmpeg-nonfree

---

### Post by VMC on 2009-10-26
> **suoko said:**
> do i have to use chrome ?
or continue with ff ?

I don't understand the question. The title and your question contradicts each other. Why would you **have** to use chrome in the first place.

BTW - chrome works perfect for me for html videos. Maybe hardware related.

---

### Post by inportb on 2009-10-26
Perhaps you should log your Chrome problems with [Google's issue tracker]("http://code.google.com/p/chromium/issues/list")?

---

### Post by suoko on 2009-10-26
seems already fixed with latest chrome 4.0.223.11
to answer question above, i prefer chrome cause it's faster at boot time and page rendering speed

---

### Post by rifak on 2009-10-26
yeah, im having problems with chome/chromium and flash also. it will play the flash videos no problem, but the interaction with them is really hit or miss. sometimes i can press buttons in the flash window, and other times its like its not recognizing my clicks. this happens with facebook videos and sometimes in hulu and youtube...im not sure what the problem is. anyone else have this?

---

### Post by RAOF on 2009-10-26
Can't play (some) html5 videos?  Install the **chromium-codecs-ffmpeg-nonfree** package for more codec support[1].

Find that clicking on flash sometimes doesn't work?  I'm pretty sure this is an nspluginwrapper bug, rather than a chromium bug; it occurs for me in Firefox, too, and I *think* that when I was trying out the nspluginwrapper-less 64bit flash beta this didn't occur.  Possible bug report is [bug #412125](https://bugs.edge.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/412125)

**EDIT:** See also [http://ubuntuforums.org/showthread.php?t=1283533](http://ubuntuforums.org/showthread.php?t=1283533)

[1] Here's hoping that chromium-codecs-gstreamer happens - as I believe is planned - making this a non-issue.

---

### Post by castrojo on 2009-10-26
I think it is an nspluginwrapper bug because I was having the problem in ff and chrome until I just got the amd64 beta directly from adobe.

---

### Post by rifak on 2009-10-26
well im not using 64bit..should this still be happening?

---

