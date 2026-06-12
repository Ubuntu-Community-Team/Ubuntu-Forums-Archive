---
title: "Ubuntu amd64 [Any Ver] still not working on nvidia RAID 0"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by smk666 on 2010-03-01
I wrestled with installation of ubuntu on my two 500GB SATA fake raid 0 disks for weeks now. 
Hardware: ASUS P5N-E SLI (nForce 650 chipset)with newest BIOS, two Seagate Barracuda 7200.12 500GB disks in (nv)RAID 0, three partitions - 40GB Windows 7 x64 C: drive, ~900GB Windows D: drive, 8GB empty/ext4) 
Here's the results (all distros are amd64 both live and alternate were tried):

Ubuntu 8.04 LTS, 8.10, 9.04, 9.10, 10.04 alpha - not working
Debian 5.04 - not working
Fedora 12 - works like charm (but for me it's a shitty distro either)

All distros uses dmraid to map disks. Problem is, that depending of Ubuntu/Debian version they see only one empty physical disk or two separate empty physical disks (/dev/sda and/or /dev/sdb)and after messing with dmraid in the console - empty fake raid disk (/dev/mapper/nvidia_ifgafbij) with size equal to only one physical drive, 500GB instead of 1TB in my case AND /dev/sdx at the same time (even with dmraid -ay -Z).
Fedora maps disks perfectly using dmraid even in graphical installer (nvidia_ifgafbij - disk, nvidia_ifgafbij1 - windows C partition, nvidia_ifgafbij2 - windows D partition, nvidia_ifgafbij3 ext4 partition). Even bootmanager (guess it was LILO, I didn't bother to check) was installed without a hitch.
Fedora proves that it is possible to make RAID-friendly distro. Why so great distro like Ubuntu can't take the example from Fedora and fix RAID issues already?

---

### Post by smk666 on 2010-03-08
ANY solution?

---

### Post by raistlin_kell on 2010-03-09
I also attempted to install Ubuntu 9.10 AMD64 from a Alternative CD on my Abit NI8 SLI mobo. The rig has 4 x 250gig SATA HDD's and I want pure performance (RAID 0) all the way. I've configed the following partitions. Mediastore parition will be a backup of my existing fileserver.

1) /dev/md0 (250mb) as /boot
2) /dev/md1 (20gb) as / (root)
3) /dev/md2 (~900gb) as /mediastore (custom partition)
4) /dev/md3 (2gb) as swap

Grub asked me where to install the MBR so i left the default /dev/md which returned an error (see below). After selecting 'back' i changed to /dev/md0 but again received the same error. 2nd attempt was to /dev/md1, also the same error. Lastly I selected LILO and that also returned an error.

error
-----------------------------------------
Unable to install GRUB in /dev/md0
Executing 'grub-install /dev/md0 failed'
This is a fatal error
-----------------------------------------

I did find this thread on the subject and will attempt tonight during another installation attempt.
[http://www.brandonchecketts.com/]("http://www.brandonchecketts.com/archives/booting-from-a-software-raid-device-on-ubunto-karmic-910")

---

### Post by smk666 on 2010-04-07
Lucid Lynx Beta1 still doesn't solve my issue. This time, in alternate installer it sees two separate disks, when I drop to console and type dmraid -ay it says that raidset nvidia_ifgafbij is broken, and it has been removed. After reboot BIOS said that array has an error, it was the part when I was REALLY scared, as I have about 800GB+ of my data without possibility to backup it. Fortunate, after another reboot, array was healthy again. Can anybody answer me why for the mother of f**k fedora installs fine from graphical installer, and ubuntu can't do this even in alternate for 3 years? I started testing every x64 version from 7.04 onwards, with different bugs. Is nvidia raid on Asus P5N-E SLI so difficult to code?

---

### Post by mathanr on 2010-04-23
The Same problem in all ubuntu version  But Fedora all version work fine, i try to Fakeride option but not use . so Ubuntu only normal HDD and SATA only?!?!?!?:confused::confused::(:(

---

