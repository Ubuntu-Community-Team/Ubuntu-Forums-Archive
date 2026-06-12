---
title: "[SOLVED] No mouse control"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by Hyper Tails on 2008-09-01
Hi i have vista and hardy (kubuntu) on my destop and laptop and i have a old computer in the basement running windows 2000  (it's original os was windows 95)
and i want to install xubuntu 8.04 and when it loads up from the live cd i can't move the muse al all.
i tryed the cordless usb mouse and that didn't work ether

128 mb ram
4gb hardrive
sentral port mouse
ps/2 keyboard

---

### Post by Hyper Tails on 2008-09-01
anybody know?

---

### Post by manishtech on 2008-09-02
You cant see the mouse or its not detecting. Both are different. If its detected, just try moving it around and you can find things getting highlighted. If its not, then it wont.

Additionally read this archives thread, it can be also useful [http://ubuntuforums.org/archive/index.php/t-438905.html](http://ubuntuforums.org/archive/index.php/t-438905.html)

---

### Post by Hyper Tails on 2008-09-02
my old computer did not orignally have usb ports so i bought a usb hub(pci) and that still dont work.
usb hub:nexxtech usb 2.0 pci card

---

### Post by oilchangeguy on 2008-09-02
if nothing else your old computer does not have the required ram to install xubuntu. see this from xubuntu's requirements;
System Requirements 
Xubuntu is available for PC, 64-Bit PC. 

CDs require 128MB RAM to run, or 192MB RAM to install. Desktop install requires at least 1.5GB of free space on your hard disk. 

in the case of a computer this old, i'd suggest something like puppy linux, or damn small linux. and if it still has it's original cd drive, that may also be one of your problems. it's to slow to run the live cd properly.

---

### Post by Hyper Tails on 2008-09-02
i tried damn small Linux but
i had the same issue

the mouse won't move

---

### Post by oilchangeguy on 2008-09-02
> **Hyper Tails said:**
> i tried damn small Linux but
i had the same issue

the mouse won't move

ok, is there a special reason why you want to install another operating system on this antique? if win 2000 is running fine leave it. you've already got a dual boot system on a much newer and better computer.

---

### Post by Hyper Tails on 2008-09-02
> **oilchangeguy said:**
> if nothing else your old computer does not have the required ram to install xubuntu. see this from xubuntu's requirements;
System Requirements 
Xubuntu is available for PC, 64-Bit PC. 

CDs require 128MB RAM to run, or 192MB RAM to install. Desktop install requires at least 1.5GB of free space on your hard disk. 

in the case of a computer this old, i'd suggest something like puppy linux, or damn small linux. and if it still has it's original cd drive, that may also be one of your problems. it's to slow to run the live cd properly.

yeah thats ture it is very slow (it was made in 1997)
i haven't tried puppy Linux but if that don't work. i'l install virtual pc 2004 on that machine to see how that goes

---

### Post by Hyper Tails on 2008-09-14
can anyone try helping me please with this still?

---

### Post by Mark Phelps on 2008-09-15
Had similar problems trying to install Xubuntu 7.04 on an old HP laptop with only 256MB of RAM.  Simply would NOT find the mouse plugged into the mouse port on the back.  Ended up using a mouse plugged directly into the one USB port, using the keyboard plugged into the keyboard jack.

Sounds like you're trying to use both USB keyboard and USB mouse plugged into a USB hub, I would be surprised if that works.  Your laptop probably has ps/2 jacks for keyboard and mouse.  You could try what I did and see if that works -- but you'll have to get hold of a "legacy" keyboard that plugs into the ps/2 jack.

The posts about not being able to install with only 128MB of RAM are correct.  You might be able to install from the alternate version -- the one that uses a text interface.  But then, it's likely to not be able to load a graphics desktop once installed.

I was able to load PC Linux OS onto my old laptop and it works OK.  They're working on a new "mini" version that just might run on the limited RAM you have.  You should google for their site and see what they have.

Last, but not least, even if you do get the laptop to install, don't be surprised if some of the hardware features simply do not work.  It's not unusual for laptop vendors to work deals with hardware vendors to supply customized drivers -- which won't work for you because they were written to work with Windows.

---

### Post by Hyper Tails on 2008-09-15
my old pc is a desktop but i'll might try it

---

### Post by Hyper Tails on 2008-09-26
Question:

do i need a ps/2 mouse?

---

### Post by Hyper Tails on 2008-09-27
...........................................................................................

---

### Post by Hyper Tails on 2008-09-27
Got it working

all i needed is an ps/2 mouse and the xubuntu 8,04 alternate cd

thanks!!!111!!!

---

