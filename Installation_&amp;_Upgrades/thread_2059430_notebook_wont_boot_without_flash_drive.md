---
title: "notebook wont boot without flash drive"
date: 2012-09-18
forum: Installation &amp; Upgrades
---

### Post by thalo on 2012-09-18
i have an HP mini notebook.  i created a bootable flash drive to install Ubuntu 12.04LTS on it.  the install went okay, everything was working to the point of restarting after install and some updates.

now, when starting the computer without the flash drive in, it stays at a blank screen with a cursor at the top left.  that is all, nothing else.  i can put the flash drive in, Ctrl/Alt/Delete to restart things.  to get it to boot up, i have to have the flash drive in, goto the boot up option menu and select the flash drive.  wont boot from the notebook HD.

i would like to reinstall to make sure i had checked all the correct boxes, etc. during the installation.  also, i think that i may have pulled out the flash drive too soon during the restart that may have not allowed somethings to be done as they should have been.

my questions are:
1.  do i need to reinstall?  is there someway to fix the HD to make sure it has what it needs to boot?

2. if not 1., how to reinstall?  i am not sure what command to use to get the installation process started.

thanks in advance for input/solutions.

---

### Post by lincoln32 on 2012-09-18
easy answer yes just reinstall. I normally do update and codec after first install.I also do not reboot I as the installer says but do a normal shut down so that I can remove flash drive but that ia minor detail. I have see that people installed back to the flash drive:lolflag:

---

### Post by darkod on 2012-09-18
No need to reinstall. The installer put grub2 on the usb since that is where you booted from to install.

Just boot once with the usb connected and open terminal. Check the device name of the hdd with:
sudo fdisk -l (small L)

Usually the hdd would be /dev/sda and the usb /dev/sdb. You can tell by the size and model.

If the hdd is /dev7sda for example, install grub2 to the MBR with:
sudo grub-install /dev/sda

Reboot without the usb and it should work.

---

### Post by C.S.Cameron on 2012-09-18
Boot with USB stick, remove it and in terminal:
```
update-grub
```

---

### Post by thalo on 2012-09-18
thanks for the code, it did the job.

---

