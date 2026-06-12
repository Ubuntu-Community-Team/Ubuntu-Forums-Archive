---
title: "[SOLVED] What hardware info do I need to post to solve installation problem ?"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by gmilne on 2008-05-20
My computer has 
E:\ partitioned drive on which only Ubuntu 7.01 is installed. 
F:\ Boot drive completely dedicated to XP
C:\ data storage + XP Programs
D:\data storage only.

(I've no idea why the letters are like this)

XP boots fine from Boot Manager.

On booting to Ubuntu computer hangs with message **initramfs** message.

1.Can anyone tell me what the next step is to solve this problem?

Mainboard :	Asus A8N-SLI Premium
Chipset :	nVidia nForce4
Processor :	AMD Athlon 64 X2 3800+ @ 2000 MHz
Physical Memory :	4096 MB (4 x 1024 DDR-SDRAM )
Video Card :	Nvidia Corp GeForce 7300 GS
Hard Disk :	ST3400832AS (400 GB)
Hard Disk :	ST3400832AS (400 GB)
Hard Disk :	ST380815AS (80 GB)
Hard Disk :	ST380815AS (80 GB)
Hard Disk :	SEAGATE (250 GB) (external Lacie drive)
DVD-Rom Drive :	HL-DT-ST DVD-RAM GSA-H55L
DVD-Rom Drive :	HL-DT-ST DVDRAM GSA-4167B
Monitor Type :	BenQ BenQ FP937s - 19 inches
Network Card :	Marvell Semiconductor (Was: Galileo Technology Ltd) Yukon 88E8001/8003/8010 PCI Gigabit Ethernet Controller (Copper)
Operating System :	Microsoft Windows XP Home Edition 5.01.2600 Service Pack 3

2. What additional hardware information do you require to help me solve this problem? I've seen SATA and RAID mentioned.
3. Is there a repair tool for Ubuntu? (disc doesn't show any corruption)
4. If I reinstall Ubuntu will it simply overwrite existing version?
Thanks

---

### Post by dstew on 2008-05-21
Can you boot an Ubuntu Live CD? If so, open a terminal and enter```
sudo fdisk -l
```Did you just recently install Ubuntu? How did you install it?

Also, the error messages before the initramfs message are significant. Can you post them to the forum?

---

### Post by gmilne on 2008-05-21
Here's the result. I'll reboot and get the message before intrmsf in a minute

ubuntu@ubuntu:~$ sudo fdisk -l 

Disk /dev/sda: 80.0 GB, 80026361856 bytes 
255 heads, 63 sectors/track, 9729 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x1cf055b4 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1        1824    14651248+  83  Linux 
/dev/sda2            1825        3040     9767520   82  Linux swap / Solaris 
/dev/sda3            3041        9729    53729392+  83  Linux 

Disk /dev/sdb: 80.0 GB, 80026361856 bytes 
255 heads, 63 sectors/track, 9729 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xdce1dce1 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1               1        9728    78140128+   7  HPFS/NTFS 

Disk /dev/sdc: 400.0 GB, 400088457216 bytes 
255 heads, 63 sectors/track, 48641 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x8a618a61 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1   *           1       48641   390708801    7  HPFS/NTFS 

Disk /dev/sdd: 400.0 GB, 400088457216 bytes 
255 heads, 63 sectors/track, 48641 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x93e093e0 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdd1               1       48641   390708801    7  HPFS/NTFS 

Disk /dev/sdf: 250.0 GB, 250059350016 bytes 
255 heads, 63 sectors/track, 30401 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xcd8a96ce 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdf1   *           1       30401   244196001    c  W95 FAT32 (LBA) 
ubuntu@ubuntu:~$

---

### Post by gmilne on 2008-05-21
Just installed it. Ideally I would like Ubuntu on one disk XP on another (which I have) and my data on a third. Is this possible
Here's the sudo result.

ubuntu@ubuntu:~$ sudo fdisk -l 

Disk /dev/sda: 80.0 GB, 80026361856 bytes 
255 heads, 63 sectors/track, 9729 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x1cf055b4 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1        1824    14651248+  83  Linux 
/dev/sda2            1825        3040     9767520   82  Linux swap / Solaris 
/dev/sda3            3041        9729    53729392+  83  Linux 

Disk /dev/sdb: 80.0 GB, 80026361856 bytes 
255 heads, 63 sectors/track, 9729 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xdce1dce1 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1               1        9728    78140128+   7  HPFS/NTFS 

Disk /dev/sdc: 400.0 GB, 400088457216 bytes 
255 heads, 63 sectors/track, 48641 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x8a618a61 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1   *           1       48641   390708801    7  HPFS/NTFS 

Disk /dev/sdd: 400.0 GB, 400088457216 bytes 
255 heads, 63 sectors/track, 48641 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x93e093e0 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdd1               1       48641   390708801    7  HPFS/NTFS 

Disk /dev/sdf: 250.0 GB, 250059350016 bytes 
255 heads, 63 sectors/track, 30401 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xcd8a96ce 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdf1   *           1       30401   244196001    c  W95 FAT32 (LBA) 
ubuntu@ubuntu:~$

---

### Post by dstew on 2008-05-22
I notice that sda and sdb are the same size, and sdc and sdd are the same size. Are this disks configured as a RAID? If so, you may have broken the RAID by installing Ubuntu to sda.

Anyway, you should post the error message you get when you try to boot Ubuntu. What is Boot Manager? Is that a Windows program? Usually, I use grub to dual boot.

---

### Post by gmilne on 2008-05-22
I don't think I have RAID (I bypass the choice to switch to RAID during boot)
During installation I picked ADVANCED as the last step. I don't know if Boot manager is GRUB but cannot be sure. On booting I simply get two lines on a DOS screen offering XP or Ubuntu, with XP being the first choice and default. (which would make me think it's MS trying to keep control):-

My error message on booting Ubuntu is
BusyBox v1.1.3 (Debian 1:1.1.3-5Ubuntu Built in shell (ash)
Enter help for a list of commands
(initramfs)

---

### Post by dstew on 2008-05-22
After you pick Ubuntu, hit <ESC> immediately and see if you get a grub menu.

---

### Post by gmilne on 2008-05-22
I get the GRUB  and have tried all the options but don't know what to do with them. None of them boot.

---

### Post by dstew on 2008-05-22
At the grub menu, press 'e' for edit (instead of 'enter'), and post the commands that make up the first menu item. There should be a title, followed by a root statement, then a kernel line, then an initrd line.

---

### Post by gmilne on 2008-05-22
find-set-root-ignore-floppies /ubuntu/install/boot/vmlinuz
kernel/ubuntu/install/boot/vmlinuz Debian - installer/custom - installation=
initrd/ubuntu/install/boo witrd.gz boot

---

### Post by dstew on 2008-05-22
Those are not typical menu items for a normal hard disk installation, but for a Wubi installation (inside Windows). I have no experience with Wubi problems, perhaps someone else can chime in.

---

### Post by gmilne on 2008-05-22
Thanks. Does this mean that I have installed Ubuntu inside Windows. I wanted Ubuntu to be parallel or the default. thanks for all your help. I'll try postin gabout WUBI
/g

---

### Post by dstew on 2008-05-22
In order to install Ubuntu in its own partition, as a truly parallel operating system, you need to *boot* the Live CD, not simply open it inside Windows. Often you need to change the BIOS boot disk order to get the CD to boot before the hard disk.

---

### Post by gmilne on 2008-05-22
Thanks. That may well have been the problem from the start and I can't recall if I installed from inside Windows or Booted from Live CD.

If I do it the way you suggest where will the GRUB be? Same partition as Ubuntu?

---

### Post by dstew on 2008-05-22
The default installs grub to the MBR (Master Boot Record) of the boot hard drive. The installer will set grub up to dual boot Windows and Ubuntu. If you want to change this, you need to hit the Advanced button on the last installation screen (I think it is step 7 of 7). It will not tell you it is installing grub, it just does it. That will result in grub being the boot loader for both Windows and Ubuntu. If you want to use another boot loader, you will need to tell it not to install grub, and configure another boot loader yourself.

---

