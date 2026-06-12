---
title: "Install ubuntu on Windows 7 with 4 partitions"
date: 2014-04-06
forum: Installation &amp; Upgrades
---

### Post by lo2 on 2014-04-06
Hi there

Due to the nature of my master's program, it would be benifical for me to be able to have Ubuntu on my laptop, which is already running Windows 7.
It is not because I have any particular problems with Windows 7, it is just because we are going to work on Linux servers and also file manipulation,
through the terminal is more handy than in Windows. 

I have however found out that I have bought a computer which already has 4 partitions, this means that I cannot create a new partition to install Ubuntu on,
because that new partionon would be formatted in some weird way, that is not very desireable (as far as I understand).

So I am not really sure what to do. My computer is an HP, where I have an HP tools, a recovery partition and a partition that I do not really know what is doing.
So does anybody have an idea about how I could get around this? I would like to end up with a computer with dual boot, where I have both Windows and Ubuntu installed,
and where I would be able to do recovery in Windows.

I have used WuBi to install Ubuntu inside of Windows, and that is what I am currently using, but as you probably know it is not the optimal solution. So yeah any advice would be appreciated?

---

### Post by ajgreeny on 2014-04-06
Firstly, make sure any partition editing you do to the windows partitions is done using windows utilities, not something like gparted; windows is very fussy about changes made to system partitions, so always reboot back to windows after making changes to allow checkdisk to run and correct any errors.

Now to your current setup.

See the answer at [http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu) which I( hope will give you everything you need, or point you in the right direction to find what more you do need.

---

### Post by Mark Phelps on 2014-04-06
ince you already have four partitions, that is the maximum allowed. Simply removing HP_TOOLS is not the solution -- as it is too small to be of any use.

So first, copy all the files and folders inside the HP_TOOLS partition into your Win7 OS partition.  

Second, open up the Win 7 Disk Management tool.  NOW, you can remove the HP_TOOLS partition.

Third, shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

Fourth, you will need a way, in the future, to restore Win7 to its present state -- and you can do that without using the Recovery partition.  Download and install the free version of Macrium Reflect.  Hook up an external drive, and use MR to image off the Win7 OS and its boot partition to that drive.  Then, use the MR option to create and burn a Linux Boot CD.

Now, using that CD, you have the ability to restore your current Win7 setup from that backup. 

Fifth, you can now go back into the Win7 Disk Management tool and remove the Recovery partition. Do not format the free space, leave it as is.

Finally, BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by mastablasta on 2014-04-06
backup and change the system partition into extended one (use the free mini partition tool/wizzard to do that). shrink the system partition and make unformated space for ubunut. boot ubuntu and selec to install next to windows.

or just use virtualbox.

---

### Post by SuperFreak on 2014-04-06
This is how I did it with my HP Laptop. See post #12 [http://ubuntuforums.org/showthread.php?t=2191419&highlight=primary+partitions]("http://ubuntuforums.org/showthread.php?t=2191419&highlight=primary+partitions")

---

### Post by lo2 on 2014-04-06
> **Mark Phelps said:**
> ince you already have four partitions, that is the maximum allowed. Simply removing HP_TOOLS is not the solution -- as it is too small to be of any use.

So first, copy all the files and folders inside the HP_TOOLS partition into your Win7 OS partition.  

Second, open up the Win 7 Disk Management tool.  NOW, you can remove the HP_TOOLS partition.

Third, shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

Fourth, you will need a way, in the future, to restore Win7 to its present state -- and you can do that without using the Recovery partition.  Download and install the free version of Macrium Reflect.  Hook up an external drive, and use MR to image off the Win7 OS and its boot partition to that drive.  Then, use the MR option to create and burn a Linux Boot CD.

Now, using that CD, you have the ability to restore your current Win7 setup from that backup. 

Fifth, you can now go back into the Win7 Disk Management tool and remove the Recovery partition. Do not format the free space, leave it as is.

Finally, BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

First off, thanks a lot! You seem to know what you are talking about, I do however have some questions:

> **Mark Phelps said:**
> Fourth, you will need a way, in the future, to restore Win7 to its present state -- and you can do that without using the Recovery partition. Download and install the free version of Macrium Reflect. Hook up an external drive, and use MR to image off the Win7 OS and its boot partition to that drive. Then, use the MR option to create and burn a Linux Boot CD.

So do I need an empty external hard drive for this? And will this work just like the current boot drive?

And since I am not that experienced with Ubuntu, is there a guide for this "Something Else" option? I have heard rumours that it smart to create two partitions for Ubuntu...

---

### Post by oldfred on 2014-04-06
Auto install options will just use unallocated space, after you have used Windows to shrink Windows. The auto install just creates / (root) and swap with whatever sizes fit. I used this for the first several years of Ubuntu use, but almost immediately created a shared partition with XP so my Firefox & Thunderbird profiles could be read from both systems. I originally used FAT32 in 2006, but converted to NTFS for shared partition in 2009 for better reliability.

If you want more partitions like a separate /home or full control of sizes then you do need to use manual install or Something Else. I prefer to use gparted to create partitions in advance, as it is a bit easier, but you still have to use Something else to choose mount (/), format (ext4) and which partition that is. Or you can create partitions as part of that.

---

### Post by Mark Phelps on 2014-04-07
> So do I need an empty external hard drive for this?You don't need an empty hard drive, just one with enough room to save a compressed image of your Win7 installation.  Compression ranges from setup to setup but, in general, you can expect around 50% compression -- my Win7 takes about 40GB and the compressed image backup files are about 20GB.

> And will this work just like the current boot drive?IF you mean the Linux Boot CD, no.  That is used to boot your PC into MR so you can run a restore -- since you can't overwrite a partition that is in use.

---

### Post by SeijiSensei on 2014-04-07
Unless you really know what you are doing, mucking around with partitions and the like can quickly turn your computer into a doorstop.

I strongly recommend installing VirtualBox in Windows, then installing Ubuntu into a new virtual machine.  [Follow these instructions]("https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions") to add the Oracle VB repositories to your system and install VB.

If you really want to repartition and install Ubuntu directly, I set forth the process I used on an HP dv6t [here](http://ubuntuforums.org/showthread.php?t=1852213&p=11299287&viewfull=1#post11299287).

---

### Post by lo2 on 2014-04-07
> **SeijiSensei said:**
> I strongly recommend installing VirtualBox in Windows, then installing Ubuntu into a new virtual machine.  [Follow these instructions]("https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions") to add the Oracle VB repositories to your system and install VB.

Yeah well I have had experience with Virtual Machines, and unfortunately, I must say all of it has been pretty negative.

All the Virtual Machines I have had, have been so slow that working on them gets hugely annoying...

So I guess if you have a fix for this, it would be most welcomed!

My comp specs are:

Intel Core i3

4 GB RAM

Around 275 GB hard drive .

No dedicated graphic card.

---

### Post by lo2 on 2014-04-07
> **Mark Phelps said:**
> IF you mean the Linux Boot CD, no.  That is used to boot your PC into MR so you can run a restore -- since you can't overwrite a partition that is in use.

No I was more referring to that new recovery partition I am making, on my external hard drive. Does this one work like the one, currently inside of Windows?

And would you also urge caution trying this approach?

---

### Post by SeijiSensei on 2014-04-08
Those specifications are fine for a machine hosting a VirtualBox VM.  I'd give the Ubuntu VM 1.5 GB of the memory and leave the rest for Windows.  Oftentimes poor VM performance comes from not allocating enough memory to the guest so it ends up swapping memory to RAM all the time.

Ubuntu is a little less memory hungry than Windows as well.  If your master's program doesn't really care which desktop environment you use, choose a more lightweight version of Ubuntu like [Lubuntu]("http://lubuntu.net/") or [Xubuntu]("http://xubuntu.org/") to run in the virtual machine.

---

### Post by lo2 on 2014-04-30
Hi I came across a friend who just bought a new HP, and then I took a look at the partitioning of it, for obvious reasons.

Here is the result:

[IMG]http://i57.tinypic.com/2z4xpwl.jpg[/IMG]

(I am sorry that it is in Danish but I hope you can figure it out)

So what is the verdict is this also spoiled? I mean there are two drives with letters C: and D:, but there are like 4 partitions where it shows the partitions of the hard disk.

---

### Post by oldfred on 2014-04-30
That is a UEFI system with gpt partitioning. The efi partition means Windows boots in UEFI boot mode.

Are you planning on installing Ubuntu to that? You should install Ubuntu in UEFI mode, but HPs are not totally friendly to anything other than Windows, so some work arounds are required.

Other HPs that most users got to work.
 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts. Key board issues try differnet USB ports maybe  front.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
HP Touchsmart 15
[http://ubuntuforums.org/showthread.php?t=2213041](http://ubuntuforums.org/showthread.php?t=2213041)

---

