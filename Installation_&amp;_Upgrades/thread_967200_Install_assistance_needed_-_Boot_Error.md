---
title: "Install assistance needed - Boot Error"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by maarco on 2008-11-01
First off I want to thank everyone that reading this for your time.

I have 2 hard drives

1 400gb - I use this one for storeage
1 60GB This is the drive I am trying to install Ubuntu on.

The 60GB drive was partitioned with 3 different partitions, one of those was windows which all where about under 20 gigs.

I decided to install Ubuntu on the 60GB and used the guided install option in the setup.

Installation was successful but after the computer restarted it's not stating DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER.

I have tried the following options to try to correct this problem...


I reinstalled it in manual mode and only saw the the following a swap and a ext3 partitions.

I then deleted the main 60GB drive and installed the following

/     10 GB
/home  10GB
/boot   100MB
/swap   2GB

After it installed it still gave the same boot message.

I hate to say I'm a newbie to this but I am. I'm a quick leaner but I'm stuck on this one. Maybe needs some sort of MBR correction?

If any can help I would be great, I'll like to have my computer up and running today.

Any help is appriciated.

---

### Post by caljohnsmith on 2008-11-01
How about first opening a terminal (applications > accessories > terminal), and posting:
```
sudo fdisk -lu
```
Also, so I can get some information about your Grub setup, please post:
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
And we can work from there. :)

---

### Post by maarco on 2008-11-02
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2333e7af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   781417664   390708801    7  HPFS/NTFS

Disk /dev/sdb: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders, total 117266688 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04f12f5c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    19535039     9767488+  83  Linux
/dev/sdb2       112390740   117258434     2433847+   5  Extended
/dev/sdb3       112197960   112390739       96390   83  Linux
/dev/sdb4        19535040   112197959    46331460   83  Linux
/dev/sdb5       112390803   117258434     2433816   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
ubuntu@ubuntu:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system
ubuntu@ubuntu:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
0000000 8102                                   
0000002
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump
0000000 0000                                   
0000002
ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2008-11-02
Currently Grub is installed to the MBR of sda, and it is configured to look for its boot files in your Linux partition sdb3. When you get the "disk boot failure", do you have your BIOS set to boot the Ubuntu drive or the Windows drive? If you have your BIOS set to boot the Ubuntu drive, then that "disk boot error" could make alot of sense, but that error doesn't make sense to me if you are booting your Windows sda drive on start up; I'm assuming that you were previously able to boot into Windows just fine before installing Ubuntu, is that true? 

If you are booting your sdb drive, try booting the Windows sda drive and let me know what happens, and we can work from there.

---

