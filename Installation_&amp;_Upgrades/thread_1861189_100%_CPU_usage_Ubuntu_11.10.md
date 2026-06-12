---
title: "100% CPU usage Ubuntu 11.10"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by xpawnrip on 2011-10-15
Hi,

I just installed Ubuntu 11.10 and everything went normal till yesterday when Nautilus started to work very slow. I looked in System Monitor i realized that Nautilus is using all my memory. I have an intel core i7 processor so i don't think the cpu memory is the problem. it's the second time it happens to me, the first time it happened i reinstalled the system. The strange thing is that it happens only when i use it with my user.
please help!

[http://img23.imageshack.us/img23/5415/s … 015115.png]("http://img23.imageshack.us/img23/5415/screenshotat20111015115.png")
[http://img696.imageshack.us/img696/5415 … 015115.png]("http://img696.imageshack.us/img696/5415/screenshotat20111015115.png")

---

### Post by raja.genupula on 2011-10-15
Hi its looking like a bug(i am thinking) and hope its resolved soon.so i wanna know one more thing to give a solution , is that nautilus behaving everytime or sometimes only . because you can kill that process to save the CPU from system monitor.

you can report a bug to launchpad by doing 
 ubuntu-bug nautilus in terminal.

all the best

---

### Post by xpawnrip on 2011-10-16
i just found out that it works very very slow only after i copy my files in the home folder, in particular my school programming homeworks (c++, c#, python, qt files).

any idea why? :(
it is super annoying

---

### Post by jivo on 2011-10-16
Just updated to 11.10, and it was terrible! Apart from other problems, I see the same: 100% CPU load on one processor! No apparent process is to be blamed. :(

---

### Post by xpawnrip on 2011-10-16
is this happening to you also after you copy files on your folders?:(
hope they'll fix this, i can't stand it anymore...

i submitted this as a bug....can't wait for the update :(
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/876007](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/876007)

---

### Post by musicwurm on 2011-10-16
This is happening to me as well. Did the upgrade, rebooted, then straight to 100% cpu. I didn't copy files or anything, just booted to 100% and it does not show anything using 100% in system monitor. Help! :(

---

### Post by raja.genupula on 2011-10-17
> **xpawnrip said:**
> is this happening to you also after you copy files on your folders?:(
hope they'll fix this, i can't stand it anymore...

i submitted this as a bug....can't wait for the update :(
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/876007](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/876007)

please be patient , it will be resolved soon.up to that you can go with alternative filemanager . kill the nautilus process from system monitor.

[http://opseast.wordpress.com/2007/07/15/file-managers-alternatives-to-nautilus-and-konqueror/](http://opseast.wordpress.com/2007/07/15/file-managers-alternatives-to-nautilus-and-konqueror/)

---

### Post by xpawnrip on 2011-10-19
This is not a problem with Nautilus. It's a problem with Unity I think.
It happens the same for Ubuntu 11.04. I tried it on other computers as well.
Tried it with Ubuntu 11.10 on gnome 3 and it works fine. It also works fine in Kubuntu 11.10.

I think the problem is Unity.

---

### Post by musicwurm on 2011-10-19
> **xpawnrip said:**
> This is not a problem with Nautilus. It's a problem with Unity I think.
It happens the same for Ubuntu 11.04. I tried it on other computers as well.
Tried it with Ubuntu 11.10 on gnome 3 and it works fine. It also works fine in Kubuntu 11.10.

I think the problem is Unity.

How can I disable Unity?

---

### Post by raja.genupula on 2011-10-20
you can disable the unity from compiz settings manager. you can open it by typing as ```
ccsm
``` in terminal and there you can uncheck the ubuntu unity checkbox.

All The Best

---

### Post by xpawnrip on 2011-10-20
i don't think disabling compiz is a solution...i need these effects :(

---

### Post by raja.genupula on 2011-10-20
Hi 

   My post will not going to disturb his remaining compiz settings and its gonna Off Unity only .

---

### Post by ringo28 on 2011-10-20
the right driver for your graphic card?

---

### Post by mpiter on 2011-10-20
Do you use Google Desktop? I had the same problem with Xorg and gdl_box processes eating my CPU.  Someone pointed me to just killing gdl_box to solve the problem.  Google Desktop is not supported anymore and google-desktop-linux should be removed from our computer.  Now my configuration works well.

---

### Post by InquiringMind on 2011-10-22
Installing the classic desktop (gnome-session-fallback) solved the problem for me.  I prefer it, anyway.

---

### Post by Scott Atkinson on 2011-10-23
FWIW, I'm seeing the 100 percent cpu usage behavior on my ancient Dell laptop, even with nothing in particular running, and under both unity and classic.

This is a marked changed from 11.04 and previous.

My thinking was that this computer, with an antique celeron, may have finally reached the tipping point. BUT even at 100 percent use, the computer remains pretty responsive. Odd.

Scott A.
Watertown NY

---

### Post by mpiter on 2011-10-23
> **Scott Atkinson said:**
> FWIW, I'm seeing the 100 percent cpu usage behavior on my ancient Dell laptop, even with nothing in particular running, and under both unity and classic.

Have you tried the function [COLOR="Green"]top[/COLOR] in a terminal?

---

### Post by worldentropy on 2012-04-26
> **raja.genupula said:**
> please be patient , it will be resolved soon.up to that you can go with alternative filemanager . kill the nautilus process from system monitor.

[http://opseast.wordpress.com/2007/07/15/file-managers-alternatives-to-nautilus-and-konqueror/](http://opseast.wordpress.com/2007/07/15/file-managers-alternatives-to-nautilus-and-konqueror/)

Exactly how do you suppose one does that when the bug has been closed? and why are you assuming this is a nautilus issue? I have a regular occurrence of this crippling bug in just about every method I tried when copying files, FTP and NFSv4 included.

Let's hear the wise reply now ..:mad:

---

