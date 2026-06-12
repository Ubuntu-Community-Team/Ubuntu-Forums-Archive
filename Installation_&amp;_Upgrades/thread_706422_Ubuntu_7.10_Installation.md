---
title: "Ubuntu 7.10 Installation"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by Adeel on 2008-02-24
HI,
     I recieved  Live CD's of Ubuntu (x86, 64-bit PC). I have AMD Athlon  64 X2 4000+ processor and im using Windows XP Professional 32-bit on it it working well. Now Problem is i want to install Ubuntu 7.10 on other Partion of my hard drive and im stuck on Ubuntu Partion phase don't know what to do on that phase. So please help how keep both OS on different partions.

Need Full Installation Help!

[email]adeelaslam@msn.com[/email]

---

### Post by Pumalite on 2008-02-24
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by metalf8801 on 2008-02-24
First back up everything just in case something goes wrong.  
Ubuntu can reparation your hard drive for you.  Use the Guide option then select the amount of space you want your Ubuntu partion to have.  Then just click forward and Ubuntu will install when its done it will restart when its done.

---

### Post by Pumalite on 2008-02-24
Safer to use Gparted Live CD and resize your XP partition:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Right click on XP, choose resize from the menu. In the new space create 2 partitions:
One for '/' (aprox 12000 MB)
one for /swap, 1 GB.
The rest for /home
Then install Ubuntu, go Manual and choose the partitions already prepared.

---

### Post by smbtol on 2008-02-24
First you shoould make two more partitions with some program in Windows XP. Make one of about 10 Gb for Ubuntu partition and another one of about 1 GB for swap. Make them NTFS/FAT, doesn't matter anyway.
When you are prompted where to install Ubuntu during the installation choose guide option. Then choose mount point as / on the 10 Gb partition and choose the 1Gb partition as swap.

---

### Post by Adeel on 2008-02-25
Hi,
    I'm installing in Ubuntu 7.10 in 200 GB of Free space hard drive.Created SWAP with a space of 1 GB.
After Creating ext3 file system (on remaining space of hard drive) It says Failed to create a file system "The ext3 file system creation in partition #2 of SCSI3 (0,0,0) (sda) failed".

---

### Post by Pumalite on 2008-02-25
When you make the new partition, you put the amount of MB on top; below it says 'mount point', there you should plant a /

---

