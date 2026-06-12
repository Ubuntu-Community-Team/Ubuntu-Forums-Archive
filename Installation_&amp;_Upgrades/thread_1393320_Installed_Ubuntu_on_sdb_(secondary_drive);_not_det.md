---
title: "Installed Ubuntu on sdb (secondary drive); not detectable"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by vikasb on 2010-01-29
Hi,
 
I have 2 Hard Disks on my computer. HD#1 is 40GB with entire disk used for Vista and partitioned as C:/. HD#2 is 250GB with the entire disk partititioned into D: 100GB and E: 150GB.
 
Before, installing Ubuntu on HD#2, I shrunk the E: to 100GB using Windows Disk Manager. I installed Ubunto 9.0.6 on the remaining 50GB unpartitioned space. 
 
During Ubuntu installation, it showed me the following:
SCSI - sda - 40GB
SCSI - sdb - 250GB
SCSI - sdc - 257 MB USB (My Pen Drive that I put in for storing the boot information of Ubuntu)
 
I chose sdb from the drop down and chose the second radio button to tell Ubuntu to install on the largest continous space available. On the Advanced button the same installation screen, I chose the USB drive sdc for installion of grub/boot information.
 
I submit. Ubuntu installs successfully and asks me to remove CD and press 'Enter'. When I do that, the system restarts, I cannot see Ubuntu as an option anywhere and Vista loads automatically. I tried changing boot options from the BIOS to change it to boot from both the USB (Error:Incorrect drive) as well as secondary hard disk (Error: NTLDR Missing), but no success.
 
I am sure, Ubuntu was installed on sdb. But now, is there any way to access it. Or was it a waste installation? What can I do to have Ubuntu without disturbing Vista on sda?
 
Please answer the question specific to my case by pointing the possible mistake. Thanks.
 
Thanks,
Vikas

---

### Post by darkod on 2010-01-29
1. Which version are you using? There is no 9.0.6 version to my knowledge. I am asking because 9.04 and 9.10 use different grub versions.

2. Why didn't you install grub to /dev/sdb, why /dev/sdc? All the time you want to boot grub /dev/sdc has to be there.

Boot into the live desktop (Try Ubuntu option), and in terminal execute:
sudo fdisk -l

Post the results here. This can be fixed easily, don't touch vista or reinstall ubuntu.No need.

---

### Post by vikasb on 2010-01-31
Hello Darko,

Thanks for your response.

I checked. I downloaded 9.10 version recently from the site. Even though I checked sdc for installation of grub, but nothing got installed on it. However, I checked the partition where I installed Ubuntu and it seems it got successfully installed since it is partitioned as Linux ext. However, I cannot boot it since it is invisible to my boot order.

Here is the fdisk output (check sdb6 where I think my Ubuntu is installed):[INDENT][FONT=Fixedsys][COLOR=Navy]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4866    39079936    7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfafcfafc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       11942    95918480    7  HPFS/NTFS
/dev/sdb2           11943       30400   148263885    f  W95 Ext'd (LBA)
/dev/sdb5           15201       30400   122093968+   7  HPFS/NTFS
/dev/sdb6           11943       15059    25037239+  83  Linux
/dev/sdb7           15060       15200     1132551   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 
[/COLOR][/FONT][/INDENT]Now, do I have an option to fix this? Can I installed Grub in sdb without going through the reinstallation process?

Thanks,
Vikas

---

### Post by darkod on 2010-01-31
Yes you can. Boot again with the 9.10 cd to the live desktop, and in terminal execute:

sudo mount /dev/sdb6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

That will install grub2 to the MBR of /dev/sdb. Then reboot and go into BIOS and make the 250GB disk first in hdd boot order. Boot without the cd inside and you should see grub2.

---

### Post by vikasb on 2010-01-31
Hello Darko,

That worked perfectly. I can boot to my originally installed Ubuntu. The good thing about Grub2 is it lists the Vista boot option also, so I can keep the settings to boot from the 2nd HD. 

Thanks for understanding the problem so well.

Thanks,
Vikas

---

