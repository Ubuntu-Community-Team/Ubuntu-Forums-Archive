---
title: "Installing / Updating multiple PCs"
date: 2012-06-05
forum: Installation &amp; Upgrades
---

### Post by PM47 on 2012-06-05
I've been running 11.10 on five PCs for a while. 

I've done a clean install of 12.04 LTS on one machine and set it up as I want it (about a days work). Is there a way to clone the setup onto the other four PCs ? Either the whole install, or the customisation after running a clean install of 12.04 ? The machines do not all have identical hardware.

Once upgraded, is there a way of running updates on one machine and saving the updates locally on a network storage device so the other four machines can update locally ? Due to where I live, I have a very slow and unreliable internet connection so the less I have to download the better.

Any help or pointers to help would be much appreciated.

---

### Post by dino99 on 2012-06-05
this question is regularly asked and googling around might show you several ways, like this one:

[http://ubuntuforums.org/archive/index.php/t-1047072.html](http://ubuntuforums.org/archive/index.php/t-1047072.html)

partimage should be your prefered solution

sudo apt-get install partimage

[https://help.ubuntu.com/community/DriveImaging](https://help.ubuntu.com/community/DriveImaging)

---

### Post by PM47 on 2012-06-05
Thanks, this all suggests I can simply clone the hard disk and drop the copy into the other PCs ? Does this work with Ubuntu, it certainly doesn't with Windoze ?

---

### Post by dino99 on 2012-06-05
Partition Image is a partition imaging utility. It has support for the
following file systems:
 * Ext2/3, the Linux standard
 * ReiserFS, a journalised and powerful file system
 * FAT16/32, DOS and Windows file systems
 * HPFS, IBM OS/2 file system
 * JFS, journalised file system, from IBM, used on AIX
 * XFS, another journalised and efficient file system, from SGI, used on Irix
 * UFS (beta), Unix file system
 * HFS (beta), MacOS File system
 * NTFS (experimental), Windows NT, 2000 and XP
Only used blocks are copied and stored into an image file.
The image file can be compressed in the GZIP/BZIP2 formats to save disk space,
and split into multiple files to be copied onto removable media (ZIP for
example), burned on a CD-R, etc.

This makes it possible to save a full Linux/Windows system with a single
operation. In case of a problem (virus, crash, error, etc.), you just have
to restore, and after several minutes, your entire system is restored
(boot, files, etc.), and fully working.

This is very useful when installing the same software on many machines: just
install one of them, create an image, and restore the image on all other
machines.

---

### Post by PM47 on 2012-06-06
Thanks for your replies, the links lead me to 'remastersys', a brilliant app that does exactly what I need to do, I hadn't found this one.

Created a 'Distribution ISO' on the upgraded PC and burnt to DVD
Copied the home folder off the target PC
Upgraded the target PC from the distribution DVD 
Copied back the home folder
Configured

The whole process took about an hour :-)

Only a couple of wrinkles, remastersys doesn't appear in the 12.04 software centre after adding the repository, no idea why, easy to install from the command line however. I have Wine installed, the exe file association isn't restored, but easy to remedy. Otherwise no problems :-)

Thanks again for your help.

---

### Post by dino99 on 2012-06-06
good to know you have found your way  ):P

can you set this thread as "solved" now via the Thread Tools icon (on top right thread)

---

### Post by PM47 on 2012-06-07
Just a further note ...

I created a bootable USB memory stick from my customised live DVD using the Ubuntu 'Startup Disk Creator' and added an extra folder containing all the additional notes, files, folders etc. etc. I need to completely set up all my PCs. I now have a 'one-stop install' for all my PCs that takes about an hour to do from scratch :-) Brilliant !!

---

