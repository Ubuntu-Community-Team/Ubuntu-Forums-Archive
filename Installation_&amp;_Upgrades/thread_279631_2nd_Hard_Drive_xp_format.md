---
title: "2nd Hard Drive xp format"
date: 2006-10-18
forum: Installation &amp; Upgrades
---

### Post by evilc on 2006-10-18
I have installed Ubuntu 6 and want to add my 2nd HD which comes from my ex winxp machine, it is formatted in NFTS I need to leave it as is for now (has files needed). My question is how do I install it so I can see and use the files on it.
TIA

---

### Post by Kateikyoushi on 2006-10-18
Use the this command to list the partitions on the drive.
```
sudo fdisk -l
```

Then follow these steps [LINK]("http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only").

---

### Post by evilc on 2006-10-18
No luck when I boot up system say's no hda1 and stops? here is a copy of my stab without 2nd drive connected.

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9355    75144006   83  Linux
/dev/sda2            9356        9729     3004155    5  Extended
/dev/sda5            9356        9729     3004123+  82  Linux swap / Solaris
clive@iprimus:~$

sda1 is my sata drive hda1 (2nd)will be a ide drive

Any idea's 

Thanks

---

### Post by taurus on 2006-10-18
Okay, I assume your second harddrive where Windows is is /dev/sdb1.  Open a terminal, Applications -> Accessories -> Terminal, and create a mount point for it.

```
sudo mkdir /media/Windows
```
Now, edit your /etc/fstab with

```
gksudo gedit /etc/fstab
```
Add the following line to the end of it and save it when done.

```

/dev/sdb1   /media/Windows   ntfs   defaults,umask=0222   0   0

```
Then, mount it with

```

sudo mount -a

```
"df -h" should show you your Windows is now in /media/Windows...

---

### Post by gn2 on 2006-10-18
One option would be to put it in an external USB enclosure, and simply copy and paste the files across.

I have a Raidsonic Icybox, and when I plug it in, all my NTFS partitions appear on my desktop automatically. Which is nice.

---

### Post by evilc on 2006-10-18
Still fails, this is part startup:
Uncompressing Linux...OK booting kernel
mount: mounting /dev/sda1 on /root failed no such device

Then a few more related and locks.?

---

### Post by taurus on 2006-10-18
You need to fix your /boot/grub/menu.lst.  If you have the LiveCD, here is what you would do.

Boot from it.  Then open a terminal with Applications -> Accessories -> Terminal and create a mount point to mount your harddrive.

```
sudo mkdir /mnt/ubuntu
```
Then, you want to mount your / partition (your harddrive) as

```
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
```
Now, paste the output of your menu.lst here as

```
sudo more /mnt/ubuntu/boot/grub/menu.lst
(hit the space bar for the next 24 lines...)
```

---

### Post by evilc on 2006-10-18
Sorry don't have LiveCD only Ubuntu 6.06 downloaded full disk

---

### Post by gn2 on 2006-10-18
> **evilc said:**
> Sorry don't have LiveCD only Ubuntu 6.06 downloaded full disk

If it's the standard 6.06 download, not the alternate or server, then it is a Live CD...

---

### Post by evilc on 2006-10-19
Sorry completley lost. I downloaded Ubuntu and made an ISO disk, tried running and all I get is install/repair etc.
I had Ubuntu v5x and got a ntfs drive to be found without any trouble before but had to go back to XP as I had no printer/scanner, this time they are showing up but for the life of me I can't get this drive which seems silly.
Before all I had to do was to use fstab and media this time I have been doing what the 2nd post link for nfts read/write has said why?
As you can tell I am completley new to the terminology of Linux and need as much (simple) help as possible.

TIA

---

### Post by gn2 on 2006-10-19
> **evilc said:**
> Sorry completley lost. I downloaded Ubuntu and made an ISO disk, tried running and all I get is install/repair etc.
I had Ubuntu v5x and got a ntfs drive to be found without any trouble before but had to go back to XP as I had no printer/scanner, this time they are showing up but for the life of me I can't get this drive which seems silly.
Before all I had to do was to use fstab and media this time I have been doing what the 2nd post link for nfts read/write has said why?
As you can tell I am completley new to the terminology of Linux and need as much (simple) help as possible.

TIA

The USB enclosure is the simplest way, and it's a useful gadget to have available for backups/storage.

As for mounting Windows drives, this is done by a GUI in PCLinuxOS, pity Ubuntu isn't as advanced.

This may be of help: [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

.

---

### Post by evilc on 2006-10-20
gn2 please don't keep on about USB enclosure I don't have one.

Further to the problem I reinstalled Ubuntu and during the installation it reconised the 2 hard drives, but on boot up it got to 2nd drive and locked. The boot loading stopped at this drive saying something liken o permmission for this drive?
Maybe this helps?

TIA

---

### Post by kondor on 2006-10-20
[http://www.linuxquestions.org/questions/showthread.php?t=473320]("http://www.linuxquestions.org/questions/showthread.php?t=473320")

A combo of PATA and SATA is a bit difficult. The above link is from another forum but similar in that Linux is on the SATA and Win. on the IDE drive. You can also do a search on this forum and should find some useful info.[http://www.ubuntuforums.org/search.php?searchid=9001096]("http://www.ubuntuforums.org/search.php?searchid=9001096")

You can also use this link to configure GRUB. [http://users.bigpond.net.au/hermanzone/p15.htm#cli]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")

You will eventually find a solution. Note that the first link is like your situation.

Good luck!

---

### Post by Kateikyoushi on 2006-10-20
There is a bug on launchpad concerning sata and pata drive system. [LINK]("https://launchpad.net/distros/ubuntu/+source/grub/+bug/8497")

---

### Post by confused57 on 2006-10-20
Have you tried changing your bios to boot first to the IDE Windows drive?  It can be difficult to switch a drive with Windows installed on one computer to a different computer and have Windows function correctly.  If your Windows IDE drive will boot this way, you can probably add an entry to your /boot/grub/menu.lst to boot Windows.
   If you just want to transfer files from the IDE Windows drive, you should be able to mount it using this tutorial:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
You might just want to mount it temporarily:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop)
The instructions are for using the live cd, but should work from your Ubuntu install.

Your Windows "should" be hda1, if your drive is connected as  master on the Primary IDE controller.  You'll need to run **sudo fdisk -l**, as described in the link, to know for sure.

---

### Post by evilc on 2006-10-21
> **confused57 said:**
> Have you tried changing your bios to boot first to the IDE Windows drive?  It can be difficult to switch a drive with Windows installed on one computer to a different computer and have Windows function correctly.  If your Windows IDE drive will boot this way, you can probably add an entry to your /boot/grub/menu.lst to boot Windows.
   If you just want to transfer files from the IDE Windows drive, you should be able to mount it using this tutorial:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
You might just want to mount it temporarily:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop)
The instructions are for using the live cd, but should work from your Ubuntu install.

Your Windows "should" be hda1, if your drive is connected as  master on the Primary IDE controller.  You'll need to run **sudo fdisk -l**, as described in the link, to know for sure.


The ide drive is only nfts format and contains just everyday file which unfortunatly I need. There is definetly a bug as it won't even get passed the boot.

---

### Post by Kateikyoushi on 2006-10-21
Did you try the workaround they recommended on launchpad ?

---

### Post by gn2 on 2006-10-21
> **evilc said:**
> The ide drive is only nfts format and contains just everyday file which unfortunatly I need. There is definetly a bug as it won't even get passed the boot.

I advise disconnecting the Windows drive while you install Ubuntu since you don't want to dual-boot.

After installing Ubuntu, connect the Windows drive, re-boot and follow the guide in the link I posted earlier about mounting partitions.

Then you can simply copy and paste the files you want across.

Oh, and treat yourself to a USB external enclosure for Christmas.
Worth their weight in gold!
.

---

### Post by evilc on 2006-10-21
gn2
I checked the link and yes that is what is wrong with the boot, I am trying to get info on how to fix it.

Thanks

---

