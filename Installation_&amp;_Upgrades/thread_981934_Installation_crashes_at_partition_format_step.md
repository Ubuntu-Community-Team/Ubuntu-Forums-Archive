---
title: "Installation crashes at partition format step"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by apingaut on 2008-11-14
I am having problems installing 8.10.  I have experience with gentoo/suse/other linux.  When the installer progresses to formatting the hard drive the installation freezes.

I go through steps 1-7 at step 6 I choose "guided, use entire hard drive" (have also tried the manual partitioning)

The installation starts and moves to "partitions formatting" and stops with the installation 5% complete.

I have:
 - 80 gig drive
 - pentium 4 3.0GHz
 - Asus p4p800-vm mother board
 - 2.5 gig memory

I have tried also 8.04, 8.10 alternative, 8.10 server and have the same problem.  This box was running the current version of gentoo before trying to install ubuntu so I know the box works.  

Any help would be appreciated.

---

### Post by Pumalite on 2008-11-14
Have you tried Gparted Live CD?:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn iso to disk and boot from it.
Delete everythying in your hard drive
Make 2 'new' partitions:
The first, formatted ext3, mount point '/'
The last 2.7 GB for /swap (in case you have a Laptop): otherwise 1 GB is enough.
Then remove Gparted, boot your Ubuntu Live CD, install, go 'Manual' and use the prepared partitions.

---

### Post by apingaut on 2008-11-14
> **Pumalite said:**
> Have you tried Gparted Live CD?:


Gparted also freezes.  

I then changed hard drives, this time 40 gig.  The same thing happens.  Partition format freezes.

---

### Post by littlebat on 2008-11-14
It seems there is some problem in your installation CD, try re-download the ISO file and install it from the ISO file in hard disk directly(no need burn it to CD-R). Here is an article for reference: Install Ubuntu on Old Computer:  [http://www.learndiary.com/en/2008/11/install-ubuntu-on-old-computer.htm](http://www.learndiary.com/en/2008/11/install-ubuntu-on-old-computer.htm) , change "hardy" into "intrepid" when download "vmlinuz" or "initrd.img" file for Ubuntu 8.10.

---

