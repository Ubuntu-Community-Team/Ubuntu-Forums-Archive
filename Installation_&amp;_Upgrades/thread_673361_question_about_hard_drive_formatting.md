---
title: "question about hard drive formatting"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by dupagnem on 2008-01-20
Hi! This is a basic question about formatting a 40 GB hard drive to install Ubuntu. First, I erased all the data on my hard drive with Active KillDisk to start with a clean slate. Second, I popped the 7.10 ISO CD and selected Install Ubuntu.Third, for the partitioning, I selected Guided (took the entire hard drive), not Manual. But I did not see a screen that offered me to format the drive. Instead, the CD showed me the Ubuntu interface, and I clicked on the Install icon. Ubuntu got installed without any problem.

In Gparted 0.3.3, I have the following information:
/dev/sda1  Filesystem ext 3       Mountpoint /    Size 36.73 GiB  Used 2.87 GiB   Unused 33.87 GiB Boot
/dev/sda2                  extended                              1.43 GiB
/dev/sda5                  linux-swap                            1.43 GiB

It may sound like a dumb question, but is the hard drive actually formatted, even though I did not see a formatting utility during the installation? Where is the OS actually installed? in /dev/sda1?

Thank you for your help.

---

### Post by imT on 2008-01-20
try to do a manual partitioning, i would use 2 ext3 partitions, one of 10 gig for "/" and the rest for "/home"

---

### Post by Pumalite on 2008-01-20
> **dupagnem said:**
> Hi! This is a basic question about formatting a 40 GB hard drive to install Ubuntu. First, I erased all the data on my hard drive with Active KillDisk to start with a clean slate. Second, I popped the 7.10 ISO CD and selected Install Ubuntu.Third, for the partitioning, I selected Guided (took the entire hard drive), not Manual. But I did not see a screen that offered me to format the drive. Instead, the CD showed me the Ubuntu interface, and I clicked on the Install icon. Ubuntu got installed without any problem.

In Gparted 0.3.3, I have the following information:
/dev/sda1  Filesystem ext 3       Mountpoint /    Size 36.73 GiB  Used 2.87 GiB   Unused 33.87 GiB Boot
/dev/sda2                  extended                              1.43 GiB
/dev/sda5                  linux-swap                            1.43 GiB

It may sound like a dumb question, but is the hard drive actually formatted, even though I did not see a formatting utility during the installation? Where is the OS actually installed? in /dev/sda1?

Thank you for your help.

Post:
sudo fdisk -lu

---

### Post by forestpixie on 2008-01-20
if you've got it installed the drive is formatted

yes the os is in sda1

you'll have everyting inside root which is mountpoint /

if you look in nautilus, the 'file manager' under filesystem you have different directories like /boot, /etc - that is where the files get installed to 

the directory called /home is where your data and files would go - a bit like C:\documents and settings

when you told the installer to use the whole disc it did what was necessary to do the install, it put the swap in and extended partition sda 5 is inside sda2

hope that helps

---

### Post by dupagnem on 2008-01-20
Thank you forestpixie and others. This is the information I was looking for.

---

