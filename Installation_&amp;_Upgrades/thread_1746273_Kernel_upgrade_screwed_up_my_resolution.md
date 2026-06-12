---
title: "Kernel upgrade screwed up my resolution"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by VyseN on 2011-05-01
Greetings,

I have used Ubuntu for almost two months now, and was very happy with it until I did my first fatal mistake; I upgraded to Natty Narwhal.

Every since my upgrade, the resolution on my computer has been shot to hell. No longer can my laptop use 1280x800, as I am stuck with 1024x768 or 800x600, and it's driving me crazy. In addition, Compiz doesn't do jack sh*t anymore (pardon my language). Can any of you esteemed geniuses show me on my way? I have googled for two days now, and I'm no closer to fixing it. Since I'm new to Linux, I figured I should ask here before I screw it up further, resulting in my embarrassed return to Windows 7.

I don't know what info would be relevant to you, but from what I've seen so far, people usually ask for this:

```
Logical@CrapPC:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)

```As well as:

```
Logical@CrapPC:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  
```I hope this is a problem some of you have solved before. I've tried searching on the board here as well, but I couldn't find anything that helped me.

---

### Post by MAFoElffen on 2011-05-01
> **VyseN said:**
> Greetings,

I have used Ubuntu for almost two months now, and was very happy with it until I did my first fatal mistake; I upgraded to Natty Narwhal.

Every since my upgrade, the resolution on my computer has been shot to hell. No longer can my laptop use 1280x800, as I am stuck with 1024x768 or 800x600, and it's driving me crazy. In addition, Compiz doesn't do jack sh*t anymore (pardon my language). Can any of you esteemed geniuses show me on my way? I have googled for two days now, and I'm no closer to fixing it. Since I'm new to Linux, I figured I should ask here before I screw it up further, resulting in my embarrassed return to Windows 7.

I don't know what info would be relevant to you, but from what I've seen so far, people usually ask for this:

```
Logical@CrapPC:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)

```As well as:

```
Logical@CrapPC:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  
```
I hope this is a problem some of you have solved before. I've tried searching on the board here as well, but I couldn't find anything that helped me.
This sticky may help:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by VyseN on 2011-05-03
I really wish it did, but I couldn't find anything that helped.

---

