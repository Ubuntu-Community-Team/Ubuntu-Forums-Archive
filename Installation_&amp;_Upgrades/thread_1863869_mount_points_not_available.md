---
title: "mount points not available"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by avjain89343 on 2011-10-18
Hi,
I have a specific problem. I am not able to install any LINUX based OS on my system due to some issues of What they are refering as mount points..

error message goes for ubuntu 10.10 and 11 as:


(initramfs) mount : mounting /dev/loop0 on //filesystem.squashfs failed: No such device

Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
_


i am using a 64 bit intel core i5 windows 7 now and i want to shift. Please help me:(

---

### Post by flangemonkey on 2011-10-18
are you able to boot to a liveCD?

or is this error when trying to boot to a LiveCD?

Mount points are what Linux refers to areas of your hard drives (and a few other things, but for now, this analogy will do).

for example:

what on your Windows side was Hard Drive (C:\)

is called mount point /

if you want to keep windows, there are guides to dual booting and repartitioning, both of which you will need to do.

If you just want Linux (like me ;) ) then you still should partition your hard drive - I'd recommend

150MB /boot
2048MB swap
20GB /
rest of hard drive for /home

this is my preference and probably a good way for beginners to start.

anyway, let us know how far you get with a LiveCD, then we can point you in the right direction :)

---

### Post by avjain89343 on 2011-10-18
BY livecd you mean a real CD or is it something else... please try to bear me um really new to all this but i really want to use ubuntu

---

### Post by flangemonkey on 2011-10-18
hi, 

yeah, a real CD, the install CD that you have, if it's a liveCD when you put it in and tell the computer to start from the CD it should put you in to a 'live' ubuntu environment where you will be able to test the 'Ubuntu experience'... 

if your computer doesn't start from the CD you'll have to press delete, F1, F2, F8 or F12 depending on your computer and you'll be presented with a text screen that will allow you to set the boot order, just move the CD drive to the top of the list and save and restart...

if this environment is what's not working you might have one designed for a different architecture (but we'll get to that if we need to ;) )

---

