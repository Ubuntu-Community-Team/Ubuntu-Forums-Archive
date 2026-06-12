---
title: "can't install Ubuntu 11.04"
date: 2011-09-06
forum: Installation &amp; Upgrades
---

### Post by barney gibbon on 2011-09-06
Hello,

I tried a fresh install of Ubuntu 11.04 using a CDROM and everything seemed to install okay and was working fine but after about a day it crashed and after would only boot to a black screen with a waste bin and a computer icon. I tried reinstalling several times but it never worked again. I downloaded a new iso and installed from a usb stick and before going to the black screen it said the hardware was incompatible. Do you think my graphics card nvidia Geforce 8400GS could be the problem? Any suggestions would be much appreciated,

bg

---

### Post by coffeecat on 2011-09-06
> **barney gibbon said:**
> before going to the black screen it said the hardware was incompatible.

Are you sure that is what it said? With a nvidia card, the default nouveau driver is not capable of the 3d acceleration needed for the Unity desktop, so you get a message telling you this (can't remember the exact words) and you are taken to the classic desktop until you install the proprietary driver.

> **barney gibbon said:**
>  Do you think my graphics card nvidia Geforce 8400GS could be the problem? 

Unlikely. I was using a system with a nvidia GeForce 8400GS. It ran the 11.04 classic desktop OK with the nouveau driver and then Unity ran just fine with the proprietary nvidia driver.

Unless perhaps your nvidia card is failing. Do you have onboard graphics or another card you could try?

---

### Post by barney gibbon on 2011-09-07
I'm surprised Unity works with your graphics card. When I first installed it, it was exactly like you said with the classic desktop and the install drivers message. I clicked on the recommended one and Unity started working, with the all the icons down the left and I was very happy with it. I can't understand why when installing again it wouldn't get that far (just to a black screen with two icons no menus). Unfortunately I haven't got a spare graphics card or onboard graphics, but I'll look at new ones. I've the Geforce one for four or five years.
I read that you can test if your system will work with Unity by typing this

/usr/lib/nux/unity_support_test -p 

and I found it says yes for 8 things 'no' for 'not software rendered' for 'GL version is 1.4+'. At the bottom it says 'Unity supported: no'

Before installing I saved all the files in the home directory in /home, following instructions on the Ubuntu website. Could that have any affect? Also, I've been using the 32 bit iso but I've got an AMD64 cpu, could that be the incompatible hardware? I also checked my hard drive with the disk utility and it says it's got 6 bad sectors and it failed the read test and it has 'Current Pending Sector Count' in red. Thanks a lot for your help, coffeecat.

---

### Post by coffeecat on 2011-09-07
> **barney gibbon said:**
> I'm surprised Unity works with your graphics card.

Why? It's a perfectly adequate graphics chipset for compiz, which is what you need to run Unity.

> **barney gibbon said:**
> 
I read that you can test if your system will work with Unity by typing this

/usr/lib/nux/unity_support_test -p 

and I found it says yes for 8 things 'no' for 'not software rendered' for 'GL version is 1.4+'. At the bottom it says 'Unity supported: no'

Was that with the nouveau driver? If you are using the nouveau driver and haven't installed the experimental package, you will not be able to run Unity.

> **barney gibbon said:**
> Before installing I saved all the files in the home directory in /home, following instructions on the Ubuntu website. Could that have any affect? 

Do you mean in a separate /home partition? Then, no. But if you save files in a /home folder in the root partition and re-install, everything will be overwritten.

> **barney gibbon said:**
> Also, I've been using the 32 bit iso but I've got an AMD64 cpu, could that be the incompatible hardware?

No. 64-bit processors can run 32-bit versions of Ubuntu.

> **barney gibbon said:**
>  I also checked my hard drive with the disk utility and it says it's got 6 bad sectors and it failed the read test and it has 'Current Pending Sector Count' in red.

That doesn't sound good at all. Backup anything important **now** before the hard drive fails. If you do have a failing drive that might explain why things were OK for a day when you first installed, and now you can't get a working installation - if I read your OP correctly.

---

### Post by barney gibbon on 2011-09-08
You're right I did type that Support Test without having the correct driver installed, I was using the live CD at the time, ahem. I tried installing an older version of Ubuntu 10.04 yesterday. I've used this before no problems and that didn't work either, it never got to the login, which made me wonder if keeping all my files on the /home partition had somehow caused the problems (it's the first time I've ever tried doing that when upgrading). I saved some files on an external drive then tried installing 11.04 and deleted the /home partition first and it worked, hurray! Unity is working well again :o) I'll definitely get a new hard drive, I don't want to lose anything. Thanks for your help coffeecat.

---

### Post by coffeecat on 2011-09-08
Good luck! :)

---

