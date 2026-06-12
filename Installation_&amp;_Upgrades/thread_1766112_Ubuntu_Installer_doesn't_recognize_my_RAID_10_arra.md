---
title: "Ubuntu Installer doesn't recognize my RAID 10 array"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by gibby_ on 2011-05-23
Ok sorry if this is a repeat post, but I have searched the forums and haven't found any similar problems.  Whenever I try to install Ubuntu, it seems to be going fine until I get to the partition step.  At this point, there are no drives (even standalone, much less my RAID array).  I am attempting to set up a dual boot with Windows 7, which I had working fine with my old motherboard and CPU.  

System specs are:
ASUS M4A78LT-M Mobo with AMD Phenom X4 955 processor
4GB of generic RAM
4x1TB drives set up in a RAID 10 array currently running Windows 7.  

Like I said I can't get past the partition portion of the install.  If I run the LiveCD, I can only see 2 of my drives in GPARTED, and it doesn't see all (3) partitions on these drives.  

Any help is greatly appreciated.

Jonathan

---

### Post by pugelarouge on 2011-08-16
I think you should find the alternate installer disk will play nicer with md / raid

Just a thought


AJ

---

### Post by YesWeCan on 2011-08-16
Hi there, welcome.
You have what is known around here as a Windows software RAID or fake RAID or dmraid. This is a different system to linux software RAID or md RAID or mdadm.
If you are installing 11.04 it has the dmraid drivers already installed.

I dont have any experience of this but if you boot live CD you should be able to see and mount the array in the Places menu. If not, open a terminal and run sudo dmraid -ay first. Then run the installer and hopefully the partitioner will see the array as a single device. There may be difficulties with the Grub boot loader installation: I believe it needs to be installed to the device name of the array, /dev/mapper/xyz

I would use Windows to reduce itself to make empty space for Ubuntu rather than GParted.

---

