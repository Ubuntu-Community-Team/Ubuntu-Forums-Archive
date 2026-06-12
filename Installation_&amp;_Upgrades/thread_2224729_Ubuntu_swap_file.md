---
title: "Ubuntu swap file"
date: 2014-05-17
forum: Installation &amp; Upgrades
---

### Post by herni2 on 2014-05-17
Hi.

I was trying to triple boot my PC: win7, winVista and Ubuntu14, but, during the installation of Ubuntu, I chose the vista partition to be the swap file. Now that windows won't start and the files I had are missing. The attachment shows the partitions on one hitachi HD, the one with 180GB is where vista used to be.

Is there a way to recover the files at least? 



Thanks.

---

### Post by tgalati4 on 2014-05-18
Normally you would select an empty partition (4 to 10 GB in size, that you created manually) to become the swap file.  By choosing the Windows partition, you effectively (and efficiently) wiped it out.

You can go through the partition recovery process using *testdisk*.  If that is not successful, then you can try individual file recovery using *photorec*.

Some reading:  [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by oldfred on 2014-05-18
STOP using system.
Do not boot with anything that mounts swap particularly live installer or your actual install. Both will mount swap and live installer uses swap to speed up system.
You can boot with gparted liveCD or parted magic liveCD as they do not auto mount swap.
If you have not actually used swap you may just be able to change partition back from swap to NTFS. Do not format just change partition type.

Also if Vista was your first Windows install, it would have had boot flag or be the  active partition in WIndows. And Windows second installs have no boot files but put all boot files into the active partition. So your Windows 7 will not be bootable, without repairs. And if installed in a logical partition, you have to create a primary NTFS partition with the boot flag to get it to boot/repair.

 Backup partition table structure to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

If Vista is/was sda1, note space after sda, see man sfdisk for details:
   change sda1 to type 07
sudo sfdisk --change-id /dev/sda 1 07

If in your system immediate turn swap off.
man swapoff
sudo swapoff -a

then you can use sfdisk commands above or use Disks or Disk utitlity to change partition type to 07 or 0x07 which ever it offers.

---

### Post by herni2 on 2014-05-18
Thank you both, I'm gonna try fix it.

---

