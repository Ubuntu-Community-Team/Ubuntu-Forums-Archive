---
title: "Need help with boot loader"
date: 2012-01-14
forum: Installation &amp; Upgrades
---

### Post by Robert Finley on 2012-01-14
HP DL360 G4
lubuntu 11.10


/dev/cciss/c0d0p1 /boot
/dev/cciss/c0d0p2 /extended
  /dev/cciss/c0d0p5 /
  /dev/cciss/c0d0p6 swap

This is the partition scheme on my RAID.  

I have installed a specialized kernel but when lubuntu boots there is no menu to select it.  I have a LiveUSB and I have tried a lot of how to's. Nothing seems to be working. Please point me in the right direction.

---

### Post by carl4926 on 2012-01-14
Are you saying your system doesn't boot at all
Or is it that you don't see the menu at boot?

If seeing the menu is the problem, try holding SHIFT as you boot

---

### Post by Robert Finley on 2012-01-14
How do I get the new kernel to show up in that menu?

---

### Post by carl4926 on 2012-01-14
Have you tried running

sudo update-grub

---

### Post by Robert Finley on 2012-01-14
wow.. that was to simple
Thanks

---

### Post by carl4926 on 2012-01-14
> **Robert Finley said:**
> wow.. that was to simple
Thanks
What can I say...

Happy it helped

---

### Post by Robert Finley on 2012-01-14
execpt that it didn't work :(

Pretty sure that was the first thing I tried

It SAW the new kernel when I typed the command.  But it wasn't there when I rebooted

---

### Post by carl4926 on 2012-01-14
So you'll need to edit it in manually

All the info you need is here
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

