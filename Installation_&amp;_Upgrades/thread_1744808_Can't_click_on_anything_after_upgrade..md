---
title: "Can't click on anything after upgrade."
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by wee017 on 2011-04-30
Just restarted after upgrade, and while it boots correctly and I can move the mouse around, I can't select anything or open any menus.  Tried with different mouses and didn't work.   Help?

---

### Post by wee017 on 2011-04-30
bump?

---

### Post by shanedk on 2011-04-30
> **wee017 said:**
> Just restarted after upgrade, and while it boots correctly and I can move the mouse around, I can't select anything or open any menus.  Tried with different mouses and didn't work.   Help?

I'm having the same problem. I'm able to log in if in the login screen I select the Ubuntu Classic without the Compiz effects, so you at least should be able to get into your system that way.

It won't work with the effects, or with the new Unity launcher at all: the mouse will move, but I can't click on anything. I'm using the current NVidia driver for my GeForce 7300SE with an Acer S211HL monitor set at 1920x1080 60Hz. This configuration worked perfectly under 10.10 and 10.4, even with all of the Compiz effects.

This happened after an upgrade from 10.10. To fix it, I backed up my data files, wiped the drive, and installed 11.04 fresh. Same problem. I can always get in with the effects off, but to neither Unity nor the Classic with effects on.

---

### Post by wee017 on 2011-05-01
How do I turn off effects through the command line then?

---

### Post by shanedk on 2011-05-01
Don't know about the command line, but at the login screen after you click on your username there's an option to select which desktop to run afterwards. Select Ubuntu Classic with no effects and you should get in. It'll remember the setting so you won't have to do it next time.

It'd be real nice to have this fixed, though.

---

### Post by shanedk on 2011-05-14
I added a bug for this problem: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/775568](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/775568)

---

### Post by krespim on 2011-09-24
> **wee017 said:**
> Just restarted after upgrade, and while it boots correctly and I can move the mouse around, I can't select anything or open any menus.  Tried with different mouses and didn't work.   Help?

I am having the same problem, do you know if that has been sorted?

Just for the sake of completion, I initially tried wubi and got the same error. I naively thought that this was some weird conflict with windows 7 64 bit and made a fresh installation from a liveusb disk created with Lili USB creator (Ubuntu 11.04 with standard settings in dual boot with windows 7). 
All went smoothly but after logging in I can see the 1st screen (with the new launcher and all), Ubuntu detects new external drives and wireless connections. I can move the mouse pointer but when I "click" anywhere there is no reaction meaning that I cannot use the Graphical interface at all.

This is really annoying me because I need to to run some command line stuff in Linux environment and was really keen to, finally and after a few half-hearted attempts, move to Linux.

So the question are: 
What am I doing wrong?
Is this a bug? 
Could it be imcompatibility with some of the hardware?
What flavour of Linux should I try next if Ubuntu keeps giving me problems?

My laptop is a Toshiba T230-10J with 8GB RAM, Intel i3-330UM Processor and Intel Graphics Media Accelerator HD.

I have Ubuntu (can't remember the version but it was ~2years ago) in my old laptop (Acer aspire 1694) and it works.

Any help will be appreciated.

---

### Post by shanedk on 2011-09-24
On the login screen, click your user name and at the bottom of the screen in the third dropdown where it says "Ubuntu" select "Ubuntu Classic (No effects)". You'll be able to get in and use the system, you just can't use Compiz or anything needing the OpenGL features.

This still hasn't been fixed, and I haven't gotten any kind of reply from anyone at Ubuntu.

---

### Post by krespim on 2011-09-25
Thanks a lot! It worked.

---

