---
title: "Ubuntu 12.04 on HP NC6400"
date: 2013-02-22
forum: Installation &amp; Upgrades
---

### Post by barnesy on 2013-02-22
Hey everyone!

I'm really new to Linux(I have installed Ubuntu before and used it a little bit here and there) and I'm trying to install Ubuntu 12.04 on a HP-Compaq nc6400 from a USB.

It runs through the install and always gets to the same line and hangs.

4.830707 drm Driver supports precise vblank timestamp query.

I've done a ton of searching and it looks like I'm not the only one who has had similar problems withe the nc6400.

Does anyone have a fix for this?

Thanks for any help!

---

### Post by 2F4U on 2013-02-22
What are the hardware specs of this machine? The error message seems to indicate a problem related to the graphics card. Have you already tried the nomodeset kernel parameter?
Here is some information about that parameter:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by barnesy on 2013-02-22
> **2F4U said:**
> What are the hardware specs of this machine? The error message seems to indicate a problem related to the graphics card. Have you already tried the nomodeset kernel parameter?
Here is some information about that parameter:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I have not tried that. I had a look at your link but I am a little confused by it. I'm trying to run 12.04 and this link is for an older version of ubuntu so things are different.

I'm just unsure where to start.

Thanks for getting back to me!

---

### Post by barnesy on 2013-02-22
> **2F4U said:**
> What are the hardware specs of this machine? The error message seems to indicate a problem related to the graphics card. Have you already tried the nomodeset kernel parameter?
Here is some information about that parameter:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Ok I have started to use the CD to boot from and I can get the screens that are displayed in this link you posted. I've gotten a little further if I select nomodeset but I get to a screen that tells me my graphics are running low and my input devices were not detected. From there I can't do anything because my keyboard and mouse do not work.

My specs are:
Intel Core 2 duo @ 2.0ghz
2gigs of RAM
ATI card (according to the bios it says ATI 05/16/06

Has anyone had any issues like this?

Thanks for any help!

---

### Post by barnesy on 2013-02-23
Is it safe to say that Ubuntu will not install on this laptop and I should just give up?

Thanks!

---

### Post by jond578 on 2013-03-02
I've been running 12.04 on my HP nc6400 now for a while.  Everything works great (except fingerprint sensor). Not sure what could be wrong with your install.

---

### Post by KungFouPanda on 2013-03-17
I have the same install (12.04 LTS) on the same model laptop as the OP, and have had all of the same exact problems.  The only way to get Ubuntu to fully boot was to add 'nomodeset' every time I booted.  I have tried every solution that I could Google, and so far the only thing that I've accomplished is that it will actually boot on it's own, but the graphics are still horrible.  If I try to run ANY game, everything gets scrambled and you have to reboot, and the X.org solution that I found crashed the system.  I found this thread because I am going on three days now of trying to find a solution.

For what it's worth, I am a total noob when it comes to Linux.  I can fix most Windows problems (XP and older), but I have never used any other OS and wanted to start learning Linux, so I downloaded it to this laptop.  So far, the experience hasn't been the best.  I can type the instructions that I find on message boards like this, but I have no idea what they mean or what I am doing and it shows.  I just want to be able to view a web page without scrolling sideways, or open a game for my kids that won't scramble the screen.  If anyone has a proven solution for the X1300 graphics card, please post it here.

Edit - Forgot to add, mine is a clean, single boot install on a wiped and formatted harddrive, so there shouldn't be any external factors as to why it won't work.

---

