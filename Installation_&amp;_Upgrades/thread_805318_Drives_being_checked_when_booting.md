---
title: "Drives being checked when booting"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by blegs38552 on 2008-05-23
Ubuntu 8.04 just installed. When I boot, I get a message "Routine check of drives" with the option to hit escape to cancel. I let it run one time - it failed with more messages then I care to recount. I just want to stop this from happening every time that I start up. How can I do this? I am a relative newbie, so please be specific.

I have installed qgrubedit - here is the startup script:

default 0
timeout 10
color white/blue

title Windows Vista/Longhorn (loader)
root (hd0,7)
chainloader +1
savedefault
makeactive

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,7)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=28051a96-bc9b-40b1-993a-893259862853 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,7)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=28051a96-bc9b-40b1-993a-893259862853 ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,7)
kernel /boot/memtest86+.bin
quiet

Is there something I can delete or comment out to stop this?

---

### Post by Pumalite on 2008-05-23
The checking of your drives is normal and desirable (every 25 to 30 boots I think). If there are error messages, maybe you need to check your drive with TestDisk or RescueCD.

---

### Post by Patb on 2008-05-23
Blegs, grub is looking for both Windows and Linux on (hd0,7) the eighth partition on your first hard drive, which in linux is probably recognised as /dev/sda8 or /dev/hda8.  But you can't have both Windows and Ubuntu on the one partition.  

Do you get as far as the grub menu?  

What sort of install did you do?  Live CD? Alternate CD? Wubi? 

Do you have Windows as a dual boot on the same computer?  If not, boot from a live CD and back up and edit your grub menu:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak1
sudo gedit /boot/grub/menu.lst
``` 
Then comment out or remove the 5 lines starting "title Windows Vista..." and reboot.  If that doesn't work, follow Catlett's "How to restore Grub from a live Ubuntu cd":
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Cheers, Pat.

---

### Post by soho2014 on 2008-11-18
> **blegs38552 said:**
> Ubuntu 8.04 just installed. When I boot, I get a message "Routine check of drives" with the option to hit escape to cancel. I let it run one time - it failed with more messages then I care to recount. I just want to stop this from happening every time that I start up. How can I do this? I am a relative newbie, so please be specific.

I have installed qgrubedit - here is the startup script:

default 0
timeout 10
color white/blue

title Windows Vista/Longhorn (loader)
root (hd0,7)
chainloader +1
savedefault
makeactive

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,7)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=28051a96-bc9b-40b1-993a-893259862853 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,7)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=28051a96-bc9b-40b1-993a-893259862853 ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,7)
kernel /boot/memtest86+.bin
quiet

Is there something I can delete or comment out to stop this?

I have the identical problem.  I am not dual booting, and everything else about my system has always worked flawlessly, but whenever I try to let it check the disks without stopping it with escape, it ends up not starting up and giving me screenfuls of error messages.  I would just like to know how to disable this disk check.

---

### Post by talz13 on 2008-11-30
> **soho2014 said:**
> I have the identical problem.  I am not dual booting, and everything else about my system has always worked flawlessly, but whenever I try to let it check the disks without stopping it with escape, it ends up not starting up and giving me screenfuls of error messages.  I would just like to know how to disable this disk check.

And you don't think that those error messages might mean there is a serious issue with your filesystem?

---

### Post by soho2014 on 2008-11-30
> **talz13 said:**
> And you don't think that those error messages might mean there is a serious issue with your filesystem?

Well, if there is a serious problem with the file system, it certainly doesn't manifest itself in any other way. And why would that affect 2 of my computers?

I got the problem fixed by installed autofsck and telling to only check on shutdown, and only check upon 1000 startups.  Now all is well.:guitar:

---

