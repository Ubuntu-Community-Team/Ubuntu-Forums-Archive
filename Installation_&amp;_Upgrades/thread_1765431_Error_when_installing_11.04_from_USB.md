---
title: "Error when installing 11.04 from USB"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by Kom Sihon on 2011-05-23
Hi buddies,I'm experiencing difficulties installing Ubuntu 11.04 on an HP Laptop originally running Windows7. I tried using CD, but it blocks somewhere and displays **Kernel Panic, etc.**
I then tried using the USB Key boot and created the Boot Disk with Ubuntu. But I have the following error when booting from the USB Key: **[B]Unknown keyword in configuration file. boot:**[/B]
I downloaded the 32-bit version of Ubuntu, but the original system is a 64-bit one. Could that be the problem? or it is something else? 
Thx for helping me.

---

### Post by Rubi1200 on 2011-05-23
Hi and welcome to the forums :-)

First check the integrity of the image to make sure it is good:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Second, I suggest you try putting the image on the USB stick with UNetbootin:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I believe there is a bug in the USB creator on Ubuntu which causes this, but am not sure if this is the same one.

Either way, try UNetbootin.

---

### Post by Kom Sihon on 2011-05-28
Thx very much guy, it really seems unetbootin is better to create startup USB Disk. Now it boots normally from the key but there's another issue after few seconds: It looks like this

Cannot reserve MMIO region
[] mmio address 0x8f09d217 already in use
....
....
....

Any idea? I remind you that it is an AMD Processor previously running a 64-bit Windows 7. I'm tryin to install the 32-bit Ubuntu. Do you think that can be the problem?

---

### Post by mörgæs on 2011-05-28
It is all right to run a 32 bit Ubuntu on 64 bit hardware. In fact I recommend doing this, unless people have an absolute need for 64 bit.

Have you done a memory test from the live boot?

Trying 10.10 is also worth the while.

---

