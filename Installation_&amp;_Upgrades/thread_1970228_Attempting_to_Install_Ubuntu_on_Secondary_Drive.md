---
title: "Attempting to Install Ubuntu on Secondary Drive"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by Luckbad on 2012-04-30
I'd like to install Ubuntu on a secondary drive. I've tried the installer and let it download the files, and I've also tried putting the ISO file in the same directory as wubi (both 32 and 64 bit versions as administrator).

I am able to install it on my primary drive fine, but it is an SSD with limited capacity, so I'd like to install it on my secondary drive (a VelociRaptor with higher capacity than the SSD).

Is this possible?

Every time I attempt to install it to the second drive, I get this error:

---------------------------
Ubuntu Installer
---------------------------
An error occurred:

Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {b76b628e-8cd1-11e1-8601-d328b6698288} device partition=E:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=

For more information, please see the log file: c:\users\username\appdata\local\temp\wubi-12.04-rev266.log
---------------------------
OK   
---------------------------

---

### Post by oldfred on 2012-04-30
Wubi uses the Windows boot loader and is really just a file inside the NTFS partition. It is intended for Windows users who want an extended test over just running the liveCD, and may want to easily uninstall. No partitioning is required.

If installing to a separate drive, why not a partitioned install? Then you have full dual boot. Windows on your SSD and Ubuntu on your rotating drive.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

From the author of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

If you do install to another drive, you have to specify which drive's MBR the grub2 boot loader is installed.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by bcbc on 2012-05-01
That error is often given when attempting to install to a dynamic drive. Is it possible that your second drive is setup with dynamic disks? (because these aren't supported by linux).

---

