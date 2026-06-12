---
title: "Linux won't boot. Help?"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by Totakeke on 2008-08-10
I've tried installing Linux a few times before using the guided partitioning, but it doesn't seem to be working. Every time I try to boot it tells me that my nVidia boot thing failed, then prompts me to insert the system disk. I do that, launch the Live CD, and install Ubuntu all over again. What am I doing wrong? Thanks.

---

### Post by Pumalite on 2008-08-10
Post your specs.
If you can; from the Live CD:
sudo fdisk -lu

---

### Post by tuxxy on 2008-08-10
It should be loading GRUB, maybe you have a bootloader that could be disabled in the BIOS?

---

### Post by Totakeke on 2008-08-10
Specs

nForce 780i SLI motherboard
2 250 GiB Western Digital SATA (will RAID eventually...)
8800 GTX
Intel Core 2 Duo E6750 2.66 GHz
2 GiB DDR2 800

Oh, did you want the results of the fdisk? Here they are anyway.
------------------------------------------------------
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x85b373c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   488394751   244196352    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x85b373c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   488394751   244196352    7  HPFS/NTFS

------------------------------------------------------

> It should be loading GRUB, maybe you have a bootloader that could be disabled in the BIOS?
And that's the thing. Before it WOULD load GRUB, but I could never get to the desktop. Now it doesn't even know that Ubuntu is installed.

---

### Post by Pumalite on 2008-08-10
You don't have Ubuntu according to your sudo fdisk

---

### Post by Totakeke on 2008-08-10
Gah, I probably shouldn't have ran that on my hard drives that have Vista installed lol. I'll try installing Ubuntu again and then I'll run fdisk and see what happens.

---

### Post by Pumalite on 2008-08-10
What do you have Vista or XP? Are you planning to install Ubuntu where Windows is; or are you installing in 2nd hard drive?

---

### Post by Totakeke on 2008-08-10
I had Vista RAID 1ed with two 250 GiB hard drives, but I wanted to RAID 1 Linux on them. But ever since my luck with Linux hasn't been so good, I'm just concentrating on installing it to one disk, to see if it's something I want to make my permanent OS.

No, I don't plan on dual booting.

---

### Post by Pumalite on 2008-08-10
If you disabled your Raid, look for 'Dualboot Two Hard Drives' in this Forum (Search)
If not; take a look at this:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=408461&highlight=raid](http://ubuntuforums.org/showthread.php?t=408461&highlight=raid)
[http://ohioloco.ubuntuforums.org/showthread.php?t=630644](http://ohioloco.ubuntuforums.org/showthread.php?t=630644)
[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)

---

### Post by Totakeke on 2008-08-10
Well, my Linux installation failed again (I still can't boot into it) but here are the new results from fdisk:

--------------------------------------------------------
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00036c8a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   476246924   238123431   83  Linux
/dev/sda2       476246925   488392064     6072570    5  Extended
/dev/sda5       476246988   488392064     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdd: 259 MB, 259522560 bytes
65 heads, 32 sectors/track, 243 cylinders, total 506880 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              32      506879      253424    7  HPFS/NTFS
Partition 1 has different physical/logical endings:
     phys=(249, 64, 32) logical=(243, 44, 32)
--------------------------------------------------------

---

### Post by Totakeke on 2008-08-11
Any help? (I've resorted to installing Windows again because I needed to use a faster computer (than the other one we have)).

---

### Post by Pumalite on 2008-08-11
Post your exact error message. Do you get to see Grub?

---

### Post by Totakeke on 2008-08-11
I can't exactly post the error messages, because I've reinstalled Windows and would have to go through the trouble of resizing partitions. (And since my first attempt at that wiped Windows, I'm reluctant.)

But they weren't very specific, they just said that the nVidia boot agent failed, then gave some copyright info about the boot agent. It did this a few times then asked me to insert a system disk. I never even got to GRUB.

---

