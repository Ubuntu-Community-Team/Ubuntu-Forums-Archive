---
title: "GRUB does not recognize Win7 as second partition"
date: 2015-05-22
forum: Installation &amp; Upgrades
---

### Post by christoph14 on 2015-05-22
Hello everyone

I just tried to set up a computer with two hard drives ("sda" & "sdb") and installed Win7 64bit on "sda" and then Ubuntu14 64bit on "sdb". After that I was expecting GRUB to start, but instead Windows started as normal from "sda". So I rebooted from "sdb" to enter Ubuntu and installed GRUB over the boot menu of "sda". Now I'm not able to start Windows anymore. I tried to use boot-repair, but this didn't solve the problem, GRUB still does not recognize Windows. The report from boot-repair you can find here: [http://paste.ubuntu.com/11284322/](http://paste.ubuntu.com/11284322/)

Help, please :)

Thanks!

---

### Post by grahammechanical on 2015-05-22
Have you run?

```
sudo update-grub
```

When you first installed Ubuntu on sdb was sda connected? If not then Grub would not have known about Windows 7. I think that it is sensible when installing different OS on different drives to have the other drive disconnected. It is one way to avoid mistakes. But we then need to go into Ubuntu and update Grub.

We can install/reinstall grub but we also need to to run update-grub to detect other operating systems. Boot Repair has detected Windows 7 so there is no logical reason why the update grub command would not detect Windows 7 on that machine

By the way, is this the reason why Boot Repair did not fix things?

> =================== User settings
The settings chosen by the user will not act on the boot.


Regards.

---

### Post by yancek on 2015-05-22
The standard method in a situation such as you report would have been to install the Ubuntu Grub bootloader code to the master boot record of sdb, the drive on which you installed Ubuntu.  You would then set your BIOS to have sdb first in boot priority to boot from it.  If you did not see an entry for windows when booting, you would boot to Ubuntu and from a terminal run:  sudo update-grub and then likely would have seen the entry.

>   Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
 

I'm not sure if the above message is part of the problem as I rarely use windows.  Did you properly shut down windows before installing Ubuntu?  The only suggestion I would have is to try to update grub from Ubuntu.

---

### Post by christoph14 on 2015-05-22
Thanks for your quick reply. I actually did not disconnect "sda" before installing Ubuntu. I tried to update GRUB now and got an error message during "sudo update-grub":

ERROR: isw: wrong number of devices in RAID set "isw_bidgfcagcj_RAIDVOL" [1/2] on /dev/sdb

Unfortunately this doesn't mean anything to me.

---

### Post by christoph14 on 2015-05-22
I was able to fix the problem by searching for the error message :) Apparently this computer was used with a RAID system before, so I had to erase the RAID metadata first ("sudo dmraid -rE"), before updating GRUB.

Thanks for your help!

---

