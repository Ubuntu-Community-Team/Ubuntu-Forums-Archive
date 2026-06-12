---
title: "Xubuntu and Ubuntu CD's freeze when booting"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by mike6485 on 2007-04-26
I'm making a system up for my gran from old bits and pieces found around the house and i keep running into a problem where this screen comes up and every thing grinds to a halt I've tried using the Ubuntu 7.04 Desktop CD and the Xubuntu 7.04 alternate CD both resulting in the following screen shot, however both CD's boot on my system fine!

Message i get:
Initializing gfx code,,,
Static memory: 0x40020 - 0x9fc00
malloc 0: 0x56610 - 0x9fc00
malloc 1: 0x8000000 - 0x9000000
mallioc 2: 0xa00000 - 0xb00000
malloc 3: 0x0 - 0x0

then the system just hangs

The Specs of the system are
AMD K6-2 350MHz
128mb Ram
Matsonic M56380SG Mobo
Onboard Gfx

Hope someone can shed some light on this problem!

---

### Post by beaudoin996 on 2007-04-26
Have you try to disable your BIOS anti-virus ?

---

### Post by mike6485 on 2007-04-26
Yeah just tried that now still the same

---

### Post by beaudoin996 on 2007-04-26
I see, you don't have enough memory.  The minimum requirement isn't 256 Meg?  Recently I try to install ubuntu with a 128 Meg PC and it didn't work.

---

### Post by mike6485 on 2007-04-26
No for the Xubuntu with the alternate CD you only need 64mb 

> To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install. The Alternate Install CD only required you to have 64 MB RAM.

---

### Post by reckless2k2 on 2007-04-26
Mike is right. You're going to need the text based installer in the alternate ISOs. With 128mb of RAM, you're going to have to you Xubuntu alternate CD unless you use the server CD and install another desktop environment like fluxbox.

---

### Post by beaudoin996 on 2007-04-26
Try to boot with the CD on your working PC and think there is an option to verify if the CD is burned correctly

---

### Post by mike6485 on 2007-04-26
Just done that, CD is fine according to that

---

### Post by beaudoin996 on 2007-04-26
I suspect your CD reader.  Try to swap the CD reader with the one you successfully made the scan

---

### Post by mike6485 on 2007-04-26
Well i know i dont need to do that, the Combo drive i'm using was the one that i had in my system till this morning when my new DVD RAM drive came! that installed Ubuntu onto my system and the problem was the same when I had another CDROM drive in the troubled system

---

### Post by beaudoin996 on 2007-04-26
How did you burn the CD ? With your new DVD drive ? I just say it's a possibility that only the drive you used to burn the CD can read correctly the CD. You can also try to burn you CD a lower speed to make sure it will be read correctly by other readers.

---

### Post by mike6485 on 2007-04-26
No it was burnt with the drive thats now in the system that cant boot off of it

---

### Post by beaudoin996 on 2007-04-26
And if you had a memory problem ? Can you do something else with your PC.  Have you try other bootable CDs.

---

### Post by mike6485 on 2007-04-26
Seems to work fine, booted using the windows 98 CD so i could update the bios

---

### Post by beaudoin996 on 2007-04-26
I've no idea.  First, you should edit you first post to include your error message.  Then it will be tracable by other users having the same problem.  If this problem can be confirmed by another user, you should report it on launchpad

---

### Post by mike6485 on 2007-04-26
ok, thanks for you time!

---

### Post by stchman on 2007-04-26
> **mike6485 said:**
> I'm making a system up for my gran from old bits and pieces found around the house and i keep running into a problem where this screen comes up and every thing grinds to a halt I've tried using the Ubuntu 7.04 Desktop CD and the Xubuntu 7.04 alternate CD both resulting in the following screen shot, however both CD's boot on my system fine!

The Specs of the system are
AMD K6-2 350MHz
128mb Ram
Matsonic M56380SG Mobo
Onboard Gfx

Hope someone can shed some light on this problem!

I have Xubuntu on a P3-450 with 256MB RAM.  Put some more RAM in the PC.  Xubuntu runs slow enough on my budget box.  PC-100 RAM is pretty cheap.  I got 256MB off of Ebay for $11.

Don't even try Ubuntu or Kubuntu as they are for systems with a lot more power.  Xubuntu will be a better choice since it is a little more lightweight.

---

