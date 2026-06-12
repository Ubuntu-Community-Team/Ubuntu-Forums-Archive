---
title: "&quot;the ext4 file system creation in partition #1 of SCSI3 (0,0,0) (sda) failed.&quot;"
date: 2013-09-06
forum: Installation &amp; Upgrades
---

### Post by tdsclan11 on 2013-09-06
I just got a new hard drive yesterday and I am trying to install Ubuntu as my primary operating system off a bootable usb drive. It successfully installed the first time and after I installed the updates, my computer froze up where it says to reboot and I had to force my pc off. When I turned it back on it kept saying error after the grub screen. 
I then reformatted my hard drive and I can get into ubuntu live but every time I try to install, it says "the ext4 file system creation in partition #1 SCSI3 (0,0,0) (sda) failed."

I have an ASUS G1Sn if that helps

---

### Post by oldfred on 2013-09-06
Welcome to the forums.

How large is new drive? Did you install in one large / (root) or smaller root and separate /home which often is suggested?

If reinstalling you often have to use something else and reuse existing partitions. That may overwrite a partition if it has some sort of corruption.

Post this from terminal in live installer.
sudo parted -l

---

### Post by tdsclan11 on 2013-09-06
My new hard drive is 750gb, and I am beginner when it comes to partitions so I might of done it wrong.

I did use something else and it still gave me that error

---

### Post by tdsclan11 on 2013-09-06
Model: ATA WDC WD7500BPKT-2 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number    Start      End       Size      Type            File system       Flags
   1         1049kB   747GB    747GB     primary
   2          747GB   750GB    3218MB   extended
   5          747GB   750GB    3218MB   logical         linux-swap(v1)

---

### Post by oldfred on 2013-09-06
Some older BIOS have IDE setting still on. If you have AHCI change to that, or LBA or large as other settings, but not RAID.

I suggest a 25GB / (root) with the rest of the drive as /home or data.

Install is similar for all recent versions. So if not exactly your version still will be almost identical.
       Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

