---
title: "Installing Ubuntu on External HDD; PC has no internal HDD"
date: 2007-11-28
forum: Installation &amp; Upgrades
---

### Post by 449 on 2007-11-28
Hey everyone I'm a huge linux noob in need of help. I have a pentium 4 with no internal harddrive that I want run Ubuntu on. So I got my 250GB HDD partitioned; 38GB for main and 1 GB for the swap:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

Device Boot Start End Blocks Id System
/dev/sda1 1 25302 203238283+ c W95 FAT32 (LBA)
/dev/sda2 * 25303 30274 39937590 83 Linux
/dev/sda3 30275 30401 1020127+ 83 Linux

So when I try to install from the live cd it gets to 15% "checking system files" and gets stuck there. I'm guessing this would have to do with my lack of internal hard drive ,but being the huge linux noob I am I don't know what to do. I have glanced through this ,but it seems way over my head.Any help in this issue would be greatly appreciated. Thanks!

ps - I did a disk defect check and it found no errors.

---

### Post by Pumalite on 2007-11-28
Do md5sum on your iso and burn a new CD-R of good quality at 4x.

---

### Post by 449 on 2007-11-28
> **Pumalite said:**
> Do md5sum on your iso and burn a new CD-R of good quality at 4x.

md5sum? No clue you'll have to explain I'm a noob. I don't have any CD R's and I dont think it's the disk because I used the same one and installed successfully on an older computer. Oh and the CD with Ubuntu is an R.

---

### Post by diatribe on 2007-11-28
/dev/sda2 * 25303 30274 39937590 83 Linux
/dev/sda3 30275 30401 1020127+ 83 Linux

from the looks of it you did not change your swap partition to 82 (swap)

---

### Post by 449 on 2007-11-28
I'm pretty sure I did but I'll load up the Gparted live cd and double check.

---

### Post by diatribe on 2007-11-28
fdisk should report like this:

/dev/sdb1   *           1        9118    73240303+  83  Linux
/dev/sdb2            9119        9242      996030   82  Linux swap / Solaris

not 83 for both

---

### Post by 449 on 2007-11-28
> **diatribe said:**
> fdisk should report like this:

/dev/sdb1   *           1        9118    73240303+  83  Linux
/dev/sdb2            9119        9242      996030   82  Linux swap / Solaris

not 83 for both

Ok well I think I had the "swap" set to ext2 so I went ahead and changed it to linux-swap in Gparted. I thought the Ubuntu live cd partitioner would change it over to swap since I selected it. Anyways it still gets stucks at 15% when I try to install. So I don't think that's it. :confused:

---

### Post by diatribe on 2007-11-28
might want to try the alternate install cd and see if it helps, or try using some of the boot switches (noacpi etc) or you could try removing quiet and splash from the bootline and see if that reports an error

---

### Post by Pumalite on 2007-11-29
Learn to do md5sum on iso:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by 449 on 2007-11-29
> **Pumalite said:**
> Learn to do md5sum on iso:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

Ok so being the linux noob I am I am having trouble navigating in terminal. The iso is located in /media/EX HDD/ubuntu-7.10-alternate-i386.iso. Someone teach me? :confused:

---

### Post by 449 on 2007-11-29
> **Pumalite said:**
> Learn to do md5sum on iso:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

I did md5sum on both the live cd installer and the alternative and both matched. And I know for a fact the alternative was burned at 4x speed so I stuck once again.

---

### Post by petteriIII on 2007-11-29
Probably the installation stops because Live-CD automounts the external drive. To take automounting off do as follows: boot with Live-CD (alternate CD doesn't operate in this) when the external HD is away and go to System/Preferences/'Removable drives and media' and un-check three first squares; then press 'close'. Then attach external HD and do the installation.

---

### Post by 449 on 2007-11-29
> **petteriIII said:**
> Probably the installation stops because Live-CD automounts the external drive. To take automounting off do as follows: boot with Live-CD (alternate CD doesn't operate in this) when the external HD is away and go to System/Preferences/'Removable drives and media' and un-check three first squares; then press 'close'. Then attach external HD and do the installation.

This worked and allowed me to install, however when I reboot I get the Grub Error 17! How do I fix this? Someone said install Grub on the main partition ,but I have no clue how to. :confused:
Current Status of Ex HDD
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       25302   203238283+   c  W95 FAT32 (LBA)
/dev/sda2   *       25303       30274    39937590   83  Linux
/dev/sda3           30275       30401     1020127+  82  Linux swap / Solaris

---

### Post by 449 on 2007-11-29
After doing some reading it appears the way to fix this would be to make a "GRUB Boot CD." How exactly would I go about doing this?

---

### Post by Pumalite on 2007-11-29
[http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html](http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html)

---

### Post by 449 on 2007-11-29
> **Pumalite said:**
> [http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html](http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html)

I'm running the Live CD so I can't copy the required file(s). A GRUB boot cd is the right way to fix this, correct? :confused:

---

### Post by Pumalite on 2007-11-29
Try Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

