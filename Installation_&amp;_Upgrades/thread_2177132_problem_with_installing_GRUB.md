---
title: "problem with installing GRUB"
date: 2013-09-27
forum: Installation &amp; Upgrades
---

### Post by G1adiss on 2013-09-27
I had replaced xubuntu with ubuntu and after the instalation I wanted to install grub using live cd. And this happens:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xc3ffc3ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   411523071   205658112    7  HPFS/NTFS/exFAT
/dev/sda3       411525118   976773119   282624001    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5       411525120   472571903    30523392   83  Linux
/dev/sda6       472573952   480962559     4194304   82  Linux swap / Solaris
/dev/sda7       480964608   976773119   247904256    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 15.5 GB, 15479597056 bytes
32 heads, 63 sectors/track, 14996 cylinders, total 30233588 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5bba1f16

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    30231935    15115936+   c  W95 FAT32 (LBA)
root@ubuntu:/home/ubuntu# grub-install /dev/sda5
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).

---

### Post by G1adiss on 2013-09-27
[IMG]http://i43.tinypic.com/ncinon.png[/IMG]

---

### Post by grahammechanical on 2013-09-27
Is it? You are running a command to install Grub into /dev/sda5. This is the fifth partition on the hard disk. It is the partition with Linux installed. This should work but is sda5 mounted?

> [COLOR=#000000]root@ubuntu:/home/ubuntu# grub-install /dev/sda5[/COLOR]
[COLOR=#000000]/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).[/COLOR]

Try using the file manager to open sda5 and then run the command again?

Regards.

---

### Post by G1adiss on 2013-09-27
I opened the directory and it still doesn't work

---

### Post by oldfred on 2013-09-27
If from liveCD you have to mount partition with grub/Ubuntu (and boot partition if separate) and install to MBR. Do not install to PBR - partition boot sector unless you have another grub2 install to chain load to.  And with grub2 install to a partition is not recommended.

 #Comments are anything after the #, enter commands in terminal session
#Install MBR from liveCD/DVD/USB, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

Often easier just to use Boot-Repair.
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by G1adiss on 2013-09-27
thanks oldfred, boot-repair worked!!

---

### Post by oldfred on 2013-09-27
Glad that worked. :)

---

