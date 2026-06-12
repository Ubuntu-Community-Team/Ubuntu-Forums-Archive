---
title: "Fried MBR"
date: 2006-04-23
forum: Installation &amp; Upgrades
---

### Post by jswan on 2006-04-23
Greetings!

So basically my story goes like this......
I tried to increase my PCI-E frequency.  This caused my MBR to get completely fried.  To get my computer to just turn on again I had to set the jumpers on my Motherboard to wipe my CMOS.  Now I am having more than a hard time getting Grub to install itself onto my current MBR.   I could just live CD and data mine all my stuff off the old drive but I had to do alot go get my ubuntu 64 to work decent.   

Anyone got a better idea?
Thanks!

---

### Post by bbbooolllooo on 2006-04-24
you may want to take a look at this thread:
[http://www.ubuntuforums.org/archive/index.php/t-24113.html]("http://www.ubuntuforums.org/archive/index.php/t-24113.html")

---

### Post by jswan on 2006-04-24
Yeah, I tried both of those methods yesterday but it kept coming back with errors.  I forget what exactly they said but it seemed like it wasn't able to write to the location.  I'll post the exact response when I get home later.

---

### Post by Jagot on 2006-04-25
You may want to try resetting the MBR first.  FIXMBR at the prompt in rescue mode on a Windows installation disk, or I use a FreeDos boot disk wich uses fdisk /mbr instead.  Then try the method in that thread again.  Can't promise it'll work but worth a try.

---

### Post by microthorne on 2006-04-25
Hi,

You may have already tried this, but just in case...

By resetting the CMOS via the jumper on the motherboard, you loose all your settings.  Go through your CMOS / BIOS configuration (usually pressing 'DEL' or 'F2' or 'F10' at boot,) and make sure your primary drive is set as the first boot device.  Make sure the drive is also listed and all the IDE channels are set to either 'Auto' or properly configured for the drive.  Also, make sure all the other settings are correct, or the system will not boot.

HTH.
-Thorne

---

### Post by jswan on 2006-04-25
yeah, it turned out that the MBR was on my other drive so I changed my primary drive to that in my BIOS and everything works.    

I feel like such a bitch when my problems turn out to be this elementary :( 


but thanks guys!  :o

---

