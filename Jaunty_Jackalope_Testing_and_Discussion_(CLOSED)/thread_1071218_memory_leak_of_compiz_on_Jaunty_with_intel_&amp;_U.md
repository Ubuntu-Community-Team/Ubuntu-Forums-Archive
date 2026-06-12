---
title: "memory leak of compiz on Jaunty with intel &amp; UXA"
date: 2009-02-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Stetzen on 2009-02-15
Hello, everyone!

I'm using fully updated Jaunty on my laptop, and recently I've noticed that compiz.real process has a huge memory leak. As I can remember from Intrepid, compiz.real used to use about 20 mb of RAM, and that's it, but on Jaunty it uses up to 300 mb of RAM and a few gigabytes of swap apter a 48 h uptime. I have Intel video, and I'm using UXA acceleration. Have anybody else noticed it, or it is my own fault?

compiz                                     1:0.7.9+git20090211-0ubuntu4
xserver-xorg-video-intel                   2:2.6.1-1ubuntu2


00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

---

### Post by nyarnon on 2009-02-16
Here compiz won't even start unless I manually do a compiz --replace.

---

### Post by Cimi86 on 2009-02-16
Same problem with fedora rawhide!!! (I don't use ubuntu)
It seems a general bug.
Use EXA!

---

### Post by PythonPower on 2009-02-16
Compiz *is* using a lot of memory! :o I just checked after being on the computer for just a few hours and it's already using ~140MB RAM.

---

### Post by halfsane on 2009-02-16
I am seeing the same thing on my intel laptop. 

I think it has been going on for a week or so, but I have been too busy to look into it at all.

---

### Post by son on 2009-02-18
same problem here. disabling uxa (via xorg.conf) solves it.

---

### Post by klange on 2009-02-18
It's not Compiz that is leaking the memory, it's UXA. Just keep that in mind.

---

### Post by Stetzen on 2009-02-22
OK than.. Thank you all! Could you please confirm a bug at [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/328232](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/328232)

---

