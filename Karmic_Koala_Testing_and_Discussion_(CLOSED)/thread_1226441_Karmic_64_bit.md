---
title: "Karmic 64 bit"
date: 2009-07-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-07-29
Last nite I downloaded the daily of the Karmic 64 bit version. My machine (triple boot) already has:
Windows 7
Jaunty 32 bit
Karmic 32 bit.
So, today when I popped in the dvd for 64 bit and installed, I was really impressed as it went so smooth. Grub2 picked up all my other installs and booted with out any drama.
Now to get the hang of using 64 bit. Trying to get flash working. 
This is my first at using any thing 64 bit. Just thought I would use my machine to it's fullest capacity. 
Any thing I should be aware of, as I know some things require different packages to work (flash)?

---

### Post by jfernyhough on 2009-07-29
For best results use Adobe's 64-bit Flash plugin:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)

You'll probably also want the ia32-libs so you can run 32-bit applications.

Otherwise everything else is about the same. :D

---

### Post by DougieFresh4U on 2009-07-29
> **jfernyhough said:**
> For best results use Adobe's 64-bit Flash plugin:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)

You'll probably also want the ia32-libs so you can run 32-bit applications.

Otherwise everything else is about the same. :D

Thank you.
Of course I am no good at .tar files

---

### Post by ranch hand on 2009-07-29
If you are using a box like mine, 32bit kind of cripples the bugger.  I have my 32bit OS' on a seprate drive so that I can disable the other 2 cpus and work just on 32.

Do not update your 32 bit stuff with 64 bit enabled or, at least in Linux, you will end up with 64bit kernals.

I am not sure how well your Winwhatever would run on 64 either.

---

### Post by DougieFresh4U on 2009-07-29
> **ranch hand said:**
> If you are using a box like mine, 32bit kind of cripples the bugger.  I have my 32bit OS' on a seprate drive so that I can disable the other 2 cpus and work just on 32.

Do not update your 32 bit stuff with 64 bit enabled or, at least in Linux, you will end up with 64bit kernals.

I am not sure how well your Winwhatever would run on 64 either.

AMD64x2 5200  320GB hard drive  4G Ram
To understand what your saying, I should not have put a 64 bit version on the same hard drive as my partitions that are 32 bit?

---

### Post by lonniehenry on 2009-07-29
Dougie - it shouldn't matter what other systems you have on your drives.  each partition will have its own system, repos, etc.  Go to the 64 bit forum and follow the sticky for intsalling 64 bit flash and java, They will work with karmic.

---

### Post by Slug71 on 2009-07-29
I just installed Java from the repo's. I had the ia32 libs installed though.

The 64bit flash is easy. I just extracted the tar.gz file to my desktop and then you need to move the libflashplayer.so file to usr/lib/mozilla/plugins folder.

---

### Post by ranch hand on 2009-07-30
> **DougieFresh4U said:**
> AMD64x2 5200  320GB hard drive  4G Ram
To understand what your saying, I should not have put a 64 bit version on the same hard drive as my partitions that are 32 bit?
There is no problem installing 64 bit stuff anywhere on a 64 bit box.  I just like a box that can be either.

The problem is with me in that I have to remember to switch to 32bit operation for that 32bit OS'.  I have made that mistake before.  It only matters when you update because you will get 64bit updates on a 64bit machine.  It is hard to have a 32bit OS when it has a 64bit kernal.

This really doesn't matter too much now as there is not that much difference.  As time goes on the differences will get greater and then it will be important.

I am happy that I can switch back and forth even if it does cut my total cpu power in half to go to 32bit operation.

---

### Post by b3n87 on 2009-07-30
Are you noticing much of a speed improvement by using 64bit?

---

