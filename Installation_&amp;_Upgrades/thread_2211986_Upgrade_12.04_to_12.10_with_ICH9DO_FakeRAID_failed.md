---
title: "Upgrade 12.04 to 12.10 with ICH9DO FakeRAID failed at grub-pc install"
date: 2014-03-18
forum: Installation &amp; Upgrades
---

### Post by joe.brutal on 2014-03-18
I have two HDDs in RAID1 configured in Intel's ICH9 Matrix RAID on [DQ35JO]("http://ark.intel.com/products/50382/intel-desktop-board-dq35jo").  I wanted to do a distribution upgrade from newest 12.04 LTS x64 and it got stuck at "Configuring grub-pc", not letting me install grub.  I sensed that something may go wrong at that point, so I made sure to have the crypto key for the home directory and went looking for solutions before the reboot required for the upgrade.  I tried grub-install, but it still would not install grub.  I installed [boot-repair]("http://help.ubuntu.com/community/Boot-Repair") and tried the recommended repair.  It asked me to enter some commands into the terminal.  I followed the instructions, but it still would not install grub correctly ([Log file]("http://paste.ubuntu.com/7112440")).  Finally after the reboot, I am greeted with "error: file not found" and the "grub rescue>" prompt.  ls produces (hd0) (hd0, msdos5) (hd0, msdos1).  Root is set to hd0,msdos1 which seems to be correct and prefix points to (hd0,msdos1)/boot/grub/ which is where I find grub.cfg and a bunch of modules in i386-pc sub-directory.

I know I can recover the files somehow with a Live-CD, but I'd like to fix the grub issue and make the system functional.

Any tips?  Thanks.
Joe

---

### Post by arias2 on 2014-03-29
Sounds like grub is looking for core.img but is not able to find it. core.img should be on your boot partition in /boot/grub/i386-pc.

You should have generated a boot info summary when you did your boot-repair. Should be in /var/log/boot-sav/. What does it say? It should tell you exactly what your mbr is doing, what file is being looked for at exactly which sector on the disk, and whether it finds the image it's looking for or not.

---

### Post by oldfred on 2014-03-31
With RAID you do have to install grub to the root of RAID or to 
  isw_cfahceehja_Volume0 which does not have the p1, p2 added to show the partitions.

If you install grub2's boot loader to sda, or sdb or to partitions like sda1 then your system cannot find grub to boot as it is booting the RAID.

---

