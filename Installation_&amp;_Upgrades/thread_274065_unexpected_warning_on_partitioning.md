---
title: "unexpected warning on partitioning"
date: 2006-10-09
forum: Installation &amp; Upgrades
---

### Post by undecidable on 2006-10-09
I have just done two test installs on a Dell Inspiron 8100 with a single 60Gb hdd, using the Ubuntu 6.06 LTS Alternate Install.  It is a tri-boot configuration with a number of partitions.  

During the partitioning setup of the install, after I give the go-ahead to write the partition changes, I get the unexpected 'Warning':

"File system doesn't have expected size for Windows to like it.
cluster size is 2k (1k expected);  number of clusters is 28034 (55959 expected);  size of FATs is 110 sectors (219 expected).
Warning!
<Ignore , Cancel>"
I ignore it and there seem to be no evil consequences.  

Does anyone know the cause of this message?  It should not happen - I do have a fat16 partition (hda11 below) but the install should not be touching it.  
Details on my setup are below in case it is helpful.
A google search on this message only turned up a few scripts with the message in it, but not hints on the cause.

thanks
mc
------------------------------------------------------------------
SETUP PRIOR TO INSTALL
Three primary partitions, 7 logical partitions set up with Partitionmagic:
hda1  primary  fat32  W2000  
hda2   primary  ext3   unused  (reserved for Ubuntu)
hda4   primary  ext3   unused   (reserved to test suse)
          extended:
.           unallocated space
hda5    logical  fat32   W data
hda6    logical  fat32  W backup
hda7    logical  ext3   unused   (reserved for Linux user files)
hda8    logical  ext3  unused   (reserved for /home for Ubuntu)
hda9    logical  ext3  unused   (reserved for /home for suse)
hda10  logical  Linux swap  unused
hda11  logical  fat16  diags, xosl boot loader etc

Windows booted many times with this partition arrangement with no problems.

BOOTLOADER
Use XOSL, which very nicely operates from the logical Fat partition 11 above.

UBUNTU CONFIG  
During the Ubuntu install I changed no sizes, and set the following mount points:
hda1  primary  fat32  W2000        do not mount
hda2   primary  ext3  Ubuntu root    /
hda4   primary  ext3   unused      do not mount
          extended:
.           unallocated space
hda5    logical  fat32   W data      do not mount
hda6    logical  fat32  W backup   do not mount
hda7    logical  ext3   user docs       /docs
hda8    logical  ext3   user home       /home
hda9    logical  ext3  unused        do not mount
hda10  logical  Linux swap            swap
hda11  logical  fat16  diags,xosl boot loader   do not mount

The only partitioning action I asked the installer to take was to format the mount partitions to ext3
(hda2, hda7, hda8 & hda10).

I installed Grub to /dev/hda2 (not mbr)
--------------------------------------------------------------

---

### Post by Thooms on 2007-01-10
I've just got the same warning when trying to install Kubuntu 6.10 from te alternate install CD.

Yes, I do have a Fat16 partition - the Dell utility drive (hardware specified in signature)

What causes this warning? is it safe to ignore it?

---

### Post by undecidable on 2007-01-10
As I mentioned, I had no problems from ignoring it.  Everything still works fine including my windopes partition and my dos partition.  

My fat16 partition was not a Dell utility partion,
but the difference between a normal fat16 or fat12 partition and a dell utility partition is very small.  

In fact I converted my dell utility partition to a fat16 partition so I could put other dos tools on it, and my xosl boot loader.  (this means itf you want to run the dell utilities then you have to boot from a dos floppy first - no real problem).  

Hope this helps.

MC

---

### Post by Papa-san on 2008-03-05
Even though it doesn't eliminate the error, you can go here to make sure you have 'clean' numbers, if you want: [http://www.onlineconversion.com/computer_base2.htm](http://www.onlineconversion.com/computer_base2.htm)

---

