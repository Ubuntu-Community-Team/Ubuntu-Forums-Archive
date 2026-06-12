---
title: "Recovering Ubuntu after installing windows"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by arvind.laddu on 2008-10-16
I am not able to recover my ubuntu bcos of this error plz help...




grub> find /boot/grub/stage1
 (hd0,5)

grub> root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested

grub>

---

### Post by Pumalite on 2008-10-17
Looks like you are trying to boot Windows from a logtical partition. Post:
sudo fdisk -lu
Post a screenshot of Gparted

---

### Post by arvind.laddu on 2008-10-21
hello sir...
i have a problem which i have threaded at the forum...in which u have replied
the link to that thread is [http://ubuntuforums.org/showthread.php?t=949845](http://ubuntuforums.org/showthread.php?t=949845)


the result of that command is

ubuntu@ubuntu:~$ sudo fdisk -lu 
omitting empty partition (5) 

Disk /dev/sda: 160.0 GB, 160041885696 bytes 
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0xd5f4d5f4 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *          63    60291944    30145941    7  HPFS/NTFS 
/dev/sda2        60291945   312576704   126142380    f  W95 Ext'd (LBA) 
/dev/sda3        81915498   122110064    20097283+   7  HPFS/NTFS 
/dev/sda5        60292071    80903339    10305634+  83  Linux 
/dev/sda6        80903403    81915434      506016   82  Linux swap / Solaris 
/dev/sda7       122110128   163830869    20860371    7  HPFS/NTFS 
/dev/sda8       163830933   230645204    33407136    7  HPFS/NTFS 
/dev/sda9       230645268   291724334    30539533+   7  HPFS/NTFS 
/dev/sda10      291724398   312576704    10426153+   7  HPFS/NTFS

---

### Post by Pumalite on 2008-10-21
I remember you had come up with an error 12. How did that happen?

---

### Post by Pumalite on 2008-10-21
Try to reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by arvind.laddu on 2008-10-23
Its not working...

---

### Post by Pumalite on 2008-10-23
I'm pretty sure you have your Windows installed inside of the extended partition. At least the one you are trying to boot.
Post a screenshot of Gparted
cat /boot/grub/menu.lst

---

