---
title: "Dual booting install"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by oldjudithp on 2008-05-09
Had to reinstall hardy on disk that already had dual boot with xppro.
Must have deleted the wrong partition and incorrectly indicated or did not indicate / or /boot to the correct partition.
Now on grub booting it does not give the windows alternative.
The menu.lst now does not show the XP alternative at the bottom of the file as it did before.
Partition editor show that windows (NTFS) is still there

"
/dev/sda1 ntfs      39.06 GiB       (NO MOUNT POINT) But boot flag
 /dev/sda2 extended  35.47 GiB 2.66 GiB used  / MOUNT POINT
     dev/sda5 ext3   33.97 GiB
     dev/sda6 linux swap 1.5 GiB
                                  "
Hope this is enough info.

---

### Post by Pumalite on 2008-05-09
Post:
sudo fdisk -l

---

### Post by oldjudithp on 2008-05-10
fdisk -l gave same info as above

DEVICE    BOOT START  END   BLOCKS     ID  SYSTEM
/dev/sda1 *         1 5099  40957685    7  HPFS/NTFS
/dev/sda2        5100 9729  37190475    5  Extended
/dev/sda5        5100 9533  35616073+  83  Linux
/dev/sda6        9534 9729   1574338+  82  Linux swap / Solaris

---

### Post by zvacet on 2008-05-10
```
gksudo gedit /boot/grub/menu.lst
```

at the end of menu list you will see 

### END DEBIAN AUTOMAGIC KERNELS LIST

and below that line add 

title  Windows
rootnoverify (hd0,0)
chainloader +1

Save and close file.Reboot and you should see windows in grub.

---

### Post by oldjudithp on 2008-05-10
Tnx.
Now windows comes up in the start if I "escape" first. Otherwise loads Ubuntu automatically. Was I bit of a problem because of the short 3 sec delay which I now changed to 10 secs to give me a chance to "escape" to get to Win if I needed to go there.
Else direct to Ubuntu automatically or is that AUTOMAGICALLY?
No problem at all now.
Tnx agn.

---

### Post by Pumalite on 2008-05-10
Good luck.

---

