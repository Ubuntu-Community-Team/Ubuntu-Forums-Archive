---
title: "&quot;No file system defined&quot;"
date: 2017-01-26
forum: Installation &amp; Upgrades
---

### Post by steve169 on 2017-01-26
I'm trying to install Ubuntu 16.04.1 from a live disk.

I select "Run alongside Windows 7."

I've formatted the partition to ext4, and I've added a small swap partition.

I eventually get an error window saying that the partition I've selected has "no file system defined" and that I should correct this using the "partitioning menu."

I can't find such a menu on either the installation disk or Gparted.

What am I doing wrong?

---

### Post by tech-j on 2017-01-26
Steve169.

Some more information is going to be needed her to provide you with an intelligent response.
1.) Have you already partitioned Windows off and are trying to use the "free space" left on the disk for your installation, or,
2.) are you using a completely separate drive for your Ubuntu install?
If your situation is the 1st.
You pointed the installer to the free space and told it to "Auto Layout" and format that free space?
Have you tried to "manual" partition the free space to provide the minimum required partitions?
e.g 
/boot (1GB) Format ext2
/swap (4~8Gb depending on the machines memory)
"/" Mount Point (Format ext4) Use all remaining space
Complete installation and when prompted for where you want the "Boot Loader (Grub)" files installed, have you specified the root disk (e.g. /dev/sda) so that you can boot to both Windows or Linux at the boot prompt?
NOTE: This is assuming that you DO NOT have a UEFI Boot partition since it is Win-7. If you are using UEFI then you have to point to the UEFI partition (usually /dev/sda1 but check that.)

If the situation is #2, then do the same thing as above but without fear of wiping out windows partitions.

---

### Post by yancek on 2017-01-26
The link below has a very detailed tutorial on using GParted.

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

The link below is a detailed tutorial on installing Ubuntu.  If you scroll a little more than half way down the page, you will images of the steps you need to take.  I don't know if you will see this with the auto-install (Install Alongside) method.  Better to select the manual (Something Else) option under Installation Type.  You highlight the partition in the main window and then click on the Change tab below it and fill in the boxes.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by steve169 on 2017-02-19
I got it done. Thanks to both of you.

---

### Post by mörgæs on 2017-02-19
Good, then please mark the thread solved.

---

