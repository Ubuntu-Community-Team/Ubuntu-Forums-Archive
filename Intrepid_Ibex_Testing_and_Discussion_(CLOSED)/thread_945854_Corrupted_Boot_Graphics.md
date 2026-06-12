---
title: "Corrupted Boot Graphics"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Hideaki on 2008-10-12
I've been getting corrupted usplash graphics when booting and shutting down my laptop. It doesn't always happen though, I'd say it has a 50/50 chance of getting a proper ubuntu usplash or a corrupted one.

The corruption also changes, I've gotten screen that are half red and half black with white lines running from the top to the bottom of the screen, or some psychedelic colors, or even the ubuntu screen but shifted to the right with lines all over it.

My laptop is an ASUS G1Sn, and I think the problems only started happening after I installed the nvidia drivers.

Does anyone have any idea why this might be happening? Thanks for any help.

---

### Post by zekopeko on 2008-10-12
same here. but i'm on a desktop. see my sig. i also think that nvidia is messing with usplash

EDIT:
[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/282420](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/282420)
i reported a bug so please leave a comment for the devs. you have a 9500M right?

---

### Post by Hideaki on 2008-10-12
Yes, I've got a 9500M. It's good to hear that I'm not the only one with this issue.

---

### Post by jhan1 on 2008-10-12
I've been getting this for all kernel versions.  Top half of screen is red, bottom is black with animated lines running thru both. Using a nvidia 280 gtx.  90 percent of the time it is corrupted.

---

### Post by zekopeko on 2008-10-12
don't forget to leave a comment on the bug so that the devs know what's happening.

---

### Post by NeoFax on 2008-10-13
I have a 7300GT/GS Nvidia card and I get no usplash.  I used to have a specific none official usplash and now I get nothing nut a black screen and a flashing underscore.

---

### Post by txHarleyMan on 2008-10-13
Same issue here.  Red, white & aqua verticle bars intermittently during boot.  Nvidia 8600GT card using the Nvidia driver that Intrepid installed.

---

### Post by Chazall1 on 2008-10-13
What I have done to correct this problem, and my boot usplash has worked from alpha 2. Install Startupmanager, in the repositorys. Go to the settings area that lets you change the graphics for the usplash, look at your systems default, set a new default to the next higher resolution, and re-boot (this will not correct the problem) yet! After the re-boot, change your usplash resolution the the lowest setting posible, reboot and I have had no problems. I have done fresh installs in both hardy and in Intrepid, and I have a fully functioning boot splash.
I hope this helps!!!!

---

### Post by Gina on 2008-10-13
I sometimes get red and white stripes but only occasionally and I get it with Hardy as well as Intrepid.  And that's with ATI graphics and the default open source driver.  I did add to the bug report a while back.

---

### Post by theBishop on 2008-10-13
I'm also having the problem.  Pretty terrible, if you ask me :(

---

### Post by uidb4056 on 2008-10-13
I also have this problem but I can workaround editing the menu.lst and keep off splash and quiet options from kernel line, then I have a text boot scrolling but no problems with graphics and beeps.

---

### Post by theBishop on 2008-10-14
I snapped a pic with my cell-phone this morning when it happened:

[img]http://i34.tinypic.com/23qxw89.jpg[/img]

Sorry it's blurry...

Is this how it looks for everyone else?

I should also say, this is not just an aesthetic issue for me.  It halts the boot process and I have to cold reboot.

---

### Post by mariner09 on 2008-10-14
I have a Lenovo T61 with Intel graphics and I also see similar things.  Mostly it happens to me when I resume from hibernation or suspend.

I will toy with the startupmanager recommendation and see if that helps.

---

### Post by uidb4056 on 2008-10-15
With the updates received today (for Ibex) the problem has been fixed and I don't need to keep out quiet and splash from the kernel line in menu.lst

---

