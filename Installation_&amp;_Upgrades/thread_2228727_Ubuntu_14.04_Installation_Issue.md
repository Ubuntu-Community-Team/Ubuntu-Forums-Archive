---
title: "Ubuntu 14.04 Installation Issue"
date: 2014-06-09
forum: Installation &amp; Upgrades
---

### Post by meganmeery on 2014-06-09
Hi all:

I used UNetbootin to get Ubuntu on my Toshiba Satellite C850, and I am now trying to install it for real. I open the installer using the icon that reads "Install Ubuntu 14.04 LTS", select my language, go through the pre-requisites, and arrive on the page with all the dev/sda's and the "device for boot loader installation" selection. Up until this point, I have been formatting /dev/sda2 to ext4, and mounting to /, as well as formatting /dev/sda3 to swap, using various devices for boot loader installation. Every time I click "Install Now", I am shown an error message that reads, "Failed to create a file system: The ext4 file system creation in partition #2 of SCSI1 (0,0,0) (sda) failed." How do I go about fixing things so that I do not get this message and am able to install Ubuntu? It seems like everything I've seen and tried has done nothing to help. I've loved this sample of Ubuntu and want to use it as my primary OS, but at the same time, I'd like to keep Win7 on my PC just in case. 
Thanks in advance.

---

### Post by brad20 on 2014-06-09
Have you tried installing from doing it from a live cd/usb. If that doesnt work try to create another bootable usb with Universal USB Installer.

---

### Post by ubfan1 on 2014-06-09
It is possible the Windows 7 installation is using "dynamic disks" which should be converted back to basic before trying to install things.  Also, with basic disks (I am assuming this is NOT a UEFI machine with a gpt partitioned disk), you may have only 4 primary partitions, one of which may be an extended partition.  In this extended partition, you may then make the logical partitions which Ubuntu can use.  You might post the output from the terminal (Ctrl-Alt-t) command "df" and post the partitions on you machine here so we may offer some suggestions.  Other things in Windows which might cause problems would be fast boot (under power settings), boot speed (under BIOS, give yourself some time to hit a function key at boot if necessary, so don't leave it at "0" or "fast").  Also, you should have hashckecked the downloaded iso with md5sum to ensure the download was perfect, and then do a media check after creating the live media.

---

### Post by meganmeery on 2014-06-09
Output for Terminal command df: ubuntu@ubuntu:~$ df
df: ‘/var/lib/polkit-1/localauthority/90-mandatory.d’: Permission denied
Filesystem     1K-blocks      Used Available Use% Mounted on
/cow             1967340    628788   1338552  32% /
udev             1955812         8   1955804   1% /dev
tmpfs             393468      1132    392336   1% /run
/dev/sda2      473677820 135174344 338503476  29% /cdrom
/dev/loop0        944256    944256         0 100% /rofs
none                   4         0         4   0% /sys/fs/cgroup
tmpfs            1967340      1340   1966000   1% /tmp
none                5120         4      5116   1% /run/lock
none             1967340        80   1967260   1% /run/shm
none              102400        76    102324   1% /run/user

GParted shows three partitions:
/dev/sda1 - ntfs, Label: System, Size, 1.46 GiB, Used 223.9MiB Unused 1,25GiB Flags: boot, diag
/dev/sda2 ntfs, Mount point: /cdrom Label S3A9558D001 Size: 451.73GiB, UsedL 128.92GiB Unused: 322.82 GiB
/dev/sda3 linux-swap Size: 12.56GiB Used 400.00KiB Unused 12.56GiB

If info is missing from partition info above, assume it was not provided by GParted.

---

### Post by yancek on 2014-06-09
> I used UNetbootin to get Ubuntu on my Toshiba Satellite C850

I would understand that to mean you did a "frugal install", putting your unetbootin created Ubuntu on the windows ntfs partition, sda2.  Is that correct?  You then indicate that you are trying to format sda2 as ext4 so that you can install Ubuntu.  Does that mean you are willing to overwrite the 128GB+ of data you have on that partition.  I think you are going to have problems trying to install to the same partition you are installing from.  Resize (shrink) sda2 and create another partition for Ubuntu.  You can do that from the installer.

---

### Post by meganmeery on 2014-06-10
I understand what you mean, however while in the installer there is a message that reads "Your installation medium is on /dev/sda2. You will not be able to create, delete or resize partitions on this disk, but you may be able to install to existing partitions there." When I attempt to edit the partitions from GParted, /dev/sda2 is locked, and I can't seem to be able to unlock using umount or lvremove commands, presumably because I am running off of it.

---

### Post by tnteverett on 2014-06-10
Use UNetbootin and put the installation ISO on a USB stick, boot to this USB stick and install from there.  If necessary, drop into a shell during installation and zero your hard disk (dd if=/dev/zero of=/dev/sd{X}) and repartition after that.  
Ex:
USB might be sda and hard disk might be sdb.
dd if=/dev/zero of=/dev/sdb

---

### Post by ubfan1 on 2014-06-10
Don't zero your whole disk -- that will remove Windows.  Figure out what partition Windows is on, free up space for Ubuntu (20-30 G is enough) from a Windows disk manager too, run chkdsk a few times, then partition the freed up space (either before or during the installation).  The only tricky part is if you run out of primary partitions (4 max). But you look like you only have 3 now, so you can simply make another on (you already have swap).  Boot from USB (or CD), select "do something else" which allows you to specify exactly what partition to install into.

---

### Post by meganmeery on 2014-06-11
New Development:
I am still unable to install Ubuntu. The new development is that I can no longer boot into Windows 7. I choose the Win7 option from the list of OSs, and am then shown the "Starting Windows" page where all 4 lights come together to form the Windows logo. The problem is, it stays there. Forever. It never moves past this screen. When I try and boot into safe mode, the last file to load is aswRvrt.sys, then a similar thing happens - the computer stops while showing me a list of all the .sys files it's loaded. I do not have access to a recovery CD, nor am I able to order one. Is there another way to fix my PC? Honestly, at this point I'd be fine with completely resetting to factory setting then worrying about Ubuntu later.

---

### Post by yancek on 2014-06-11
The message you reported earlier explained the problem.  You cannot install to or format a partition on which you have the installation medium, in your case the unetbootin image on sda2.  When I got a computer with windows 7 on it, the first thing I did was create a Recovery Disk.  Always a good idea.  You should be able to get a full installation disk at time of purchase and later actually but I'm not sure about the cost or if there is a time limit.  neosmart used to have a free download of the windows recovery disk but I believe microsoft complained about that and they now charge for it.  You might try an online search for windows 7 repair disk.

---

