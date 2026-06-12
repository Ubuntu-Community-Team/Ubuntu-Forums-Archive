---
title: "tty1 login after installing driver"
date: 2011-10-07
forum: Installation &amp; Upgrades
---

### Post by papin97 on 2011-10-07
[FONT="Microsoft Sans Serif"][SIZE="3"]Hello, I was recently installing Ubuntu 10.10 and nVidia driver, and it needs to restarted, but after restarted, tty1 login is appear and I annoyed with that and I want to normal boot to gnome desktop. Anyone can help me to permanently disable tty1?
Thanks Before.[/SIZE][/FONT]

---

### Post by MAFoElffen on 2011-10-08
> **papin97 said:**
> [FONT=Microsoft Sans Serif][SIZE=3]Hello, I was recently installing Ubuntu 10.10 and nVidia driver, and it needs to restarted, but after restarted, tty1 login is appear and I annoyed with that and I want to normal boot to gnome desktop. Anyone can help me to permanently disable tty1?
Thanks Before.[/SIZE][/FONT]
Welcome to Ubuntu Forums!

I can help you, but not to "permanently disable tty1."  That is not what you need, want, nor is it possible.

Brief simple explanation:  
The text console you are erroring into during your boot, is the text console of the Linux Kernel.  Your gnome desktop is a layer that runss on a graphics layer, that runs above the kernel layer...  Is that basic enough?

So as you said offhand is your main coplaint- 
Your "gnome session" is not coming working. Because gnome is not working, it is dropping back down to the TTY text Console (it is a good thing that it "can" do that, instead of completely lock upz) It it is suspected that something is wrong with part of your grapphcs session.  That would cause that problem.

I will give instructions to use your Text console to (hopefully) diagnose and fix your system.  To do this we both need to have an understanding of what you are doing. If not ask me. 

First I need to ask you some questions:
- What is your level of experience with computers?
- Was this a new / fresh install of 10.10.
- How did you install this? (Upgrade from previous version, LiveCD, Alternate Install CD)
- What edition of 10.10 was it (desktop or sever, 32bit or 64bit)?
- What did you install on and what do you know of it's hardware... especially the amount of memory and what kind of video card it has.

Command line Linux assumes that you know what you are doing.  I will try to talk you ansd guide you through that.

---

### Post by papin97 on 2011-10-11
-I'm Medium Experiencing with computer
-New Install of 10.10
-LiveCD, I get it from shipit.ubuntu.com 1 day before closed
-Ubuntu 10.10 i386 Desktop Edition
-My Video Card is nVidia GeForce GT 540M
Is it Enough?

---

