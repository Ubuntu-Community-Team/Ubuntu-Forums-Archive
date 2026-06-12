---
title: "FORMAT NOT SUPPORTED after install"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by LewisPA on 2009-12-05
I am a new user.  I downloaded and installed Ubuntu onto my 2003 vintage Dell computer from Windows XP.  I rebooted and selected Ubuntu from the IPL menu.  After a few seconds, a white rectangle appeared on a black screen with the message FORMAT NOT SUPPORTED.  After this, I could do nothing but power off & on and return to Windows.
 
Can anyone help me get past this?

---

### Post by darkod on 2009-12-05
What is IPL menu?

---

### Post by LewisPA on 2009-12-05
It's the menu you get when you IPL (or power on) the computer.  You choose between bringing up Windows or Ubuntu.  Did I use the wrong terminology?

---

### Post by dhavalbbhatt on 2009-12-05
> **LewisPA said:**
> It's the menu you get when you IPL (or power on) the computer.  You choose between bringing up Windows or Ubuntu.  Did I use the wrong terminology?

I am guessing you were referring to the GRUB menu.

I also think we need some more information, what version of Ubuntu are you running? By the looks of it, it seems like you are having graphics issues. Can you tell us what video card you are using?

---

### Post by darkod on 2009-12-05
It's usually called grub menu, grub is the bootloader for ubuntu. I thought it's some sort of custom bootloader which might explain the problem. :)

You didn't installed Ubuntu by clicking wubi.exe inside windows right? Because that's slightly different.

---

### Post by LewisPA on 2009-12-05
I never would have figured out that it was called GRUB.  Oh well, us newbies start off knowing nothing.
 
It's version 9.10 and yes, I did click wubi.exe from inside Windows.  That's what the instructions said to to do (I think).
 
Graphics card is a 64mb GeForce4 MX.

---

### Post by darkod on 2009-12-05
I don't know much about wubi, sorry. It's different to ubuntu install.

---

### Post by dhavalbbhatt on 2009-12-05
> **LewisPA said:**
> I never would have figured out that it was called GRUB.  Oh well, us newbies start off knowing nothing.
 
It's version 9.10 and yes, I did click wubi.exe from inside Windows.  That's what the instructions said to to do (I think).
 
Graphics card is a 64mb GeForce4 MX.

Have you ever had wubi working for you before? The reason I ask is because there was new kernal that was released today and apparently there was a minor issue with it for wubi users. The following link has a good discussion going on right now, in case you want to follow -

[http://ubuntuforums.org/showthread.php?t=1346371](http://ubuntuforums.org/showthread.php?t=1346371)

The other thing that I would suggest you do is, instead of installing Ubuntu, try to use the LiveCD environment on your computer for a couple of hours to see if the OS will work with your hardware. If you feel comfortable using the OS with your hardware, you should then "install" the OS as a dual boot as against using it as a wubi install - there are good arguments both ways - but that would be my personal preference.

---

### Post by LewisPA on 2009-12-05
As I said, I'm a new user.  I have never used anything other than Windows before.
 
I don't know what you mean by the LiveCD environment.

---

### Post by darkod on 2009-12-05
Boot with the ubuntu cd, select Try Ubuntu option. That will make it run from the cd without changing your computer. It will load full ubuntu, you can even browse, check if audio is working fine, video driver, etc. If there are some drivers or incompatibility problems it will show. Usually called LiveCD.
You need to make sure in BIOS your cd-rom is before your hdd as boot device otherwise it will boot your hdd instead of the cd.

---

### Post by LewisPA on 2009-12-05
I guess I'll have to get the CD.  Thanks.

---

### Post by LewisPA on 2009-12-05
I created the CD and IPLed with it in the drive.  Same thing happened.  Seemed to be going OK, then got the FORMAT NOT SUPPORTED message and nothing after that.

---

### Post by LewisPA on 2009-12-07
Does anyone have a suggestion on how to get around this error?

---

### Post by tang99 on 2010-02-15
I also have the "FORMAT NOT SUPPORTED" message after a full install of Ubuntu 9.10 64bit from cd.

---

