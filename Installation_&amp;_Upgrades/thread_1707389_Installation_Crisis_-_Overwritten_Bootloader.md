---
title: "Installation Crisis - Overwritten Bootloader"
date: 2011-03-15
forum: Installation &amp; Upgrades
---

### Post by Terc on 2011-03-15
I just attempted to install to a USB drive, and somehow in the process, GRUB overwrote my Windows 7 bootloader on the internal disk.  My work laptop is now booting into a grub recovery whenever my USB key isn't present (with error: no such device and the uuid) - and hangs on a blinking cursor whenever the key is plugged in.

I'm not familiar with what my options are for grub rescue, but ls shows (hd0) (hd0,msdos2) (hd0,msdos1) (fd0)


My laptop is encrypted, so I don't have much chance of recovery unless I can get back to the windows bootloader.  Please, please tell me there's some fix.


UPDATE:
Here's how to fix it: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by dabl on 2011-03-15
I hope this is not too late:  [http://lifehacker.com/#!5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/#!5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

---

### Post by Terc on 2011-03-15
Actually, I wasn't even attempting to install on the internal disk at all.  The installer made some sort of decision to put the bootloader on the internal disk even though I had selected the USB drive as my installation destination.

I'm currently looking at a disk with an unknown partition and a BDEDrive partition (I've booted from a live cd).

---

### Post by dabl on 2011-03-15
Also scroll down this to "Reinstating Windows:  [https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions)

---

### Post by Terc on 2011-03-15
How (if there is any way at all) can I restore my Windows bootloader?  My first priority is just getting back to a usable windows computer, I'll figure out how to install Ubuntu to a USB again later.  I've done lots of installs to USB before... I can't understand what went wrong.

---

### Post by dabl on 2011-03-15
I would try using a Super Grub Disk to boot into Windows, then I believe there are "recovery" techniques available, once you are running Win 7.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by drs305 on 2011-03-15
> **Terc said:**
> How (if there is any way at all) can I restore my Windows bootloader?  My first priority is just getting back to a usable windows computer, I'll figure out how to install Ubuntu to a USB again later.  I've done lots of installs to USB before... I can't understand what went wrong.

If you can boot the Ubuntu LiveCD, this should point the MBR back to your Windows boot files:

These commands assume Windows is on sda (first drive). Disregard the messages about fully installing lilo. Run only these two commands and reboot.
```

sudo apt-get install lilo
sudo lilo -M /dev/sd**a** mbr
```

---

### Post by Terc on 2011-03-15
> **drs305 said:**
> If you can boot the Ubuntu LiveCD, this should point the MBR back to your Windows boot files:

These commands assume Windows is on sda (first drive). Disregard the messages about fully installing lilo. Run only these two commands and reboot.
```

sudo apt-get install lilo
sudo lilo -M /dev/sd**a** mbr
```

Thank you, I'll check and see if that works for me.

Actually, on second thought...  My system is encrypted with bitlocker, so there's no way for the bootloader to read my ini file unless it's the Windows bootloader.  I'm completely unfamiliar with the inner workings of bitlocker (more of a Truecrypt fan myself).  So I'm wondering if lilo will be able to get things off the ground for me, or if it will have issues booting too?  I can see a partition at the end of my disk called BEDDRIVE (something like that at least) which is an NTFS partition, I assume it does the work of accepting my unlock info and decrypting the drive.

Just found this: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Looks like exactly what I (hopefully) need.

Update,yup, that fixed it. (just in case someone else stumbles across this thread).

---

