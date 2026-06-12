---
title: "Xubuntu install, no partition labels"
date: 2012-08-20
forum: Installation &amp; Upgrades
---

### Post by DW1988 on 2012-08-20
So I'm trying to install xubuntu alongside windows 7 on a brand new laptop. The default partitions are unlabelled...? I want Xubuntu to be smaller, but I don't no which is which, webcam photo included for clarification.

[IMG]http://i.imgur.com/y2kTU.jpg?1[/IMG]

They're both just white boxes?

---

### Post by darkod on 2012-08-20
DO NOT resize windows with the installer!!! :)

Boot windows, open Disk Management and shrink the windows partition for as much as you want to allocate to ubuntu. Leave the newly created space as unallocated, DO NOT create ntfs partition from windows.
Restart windows few times to acknowledge the shrink.

After that start the xubuntu installer (boot with the cd) and it should install automatically into the unallocated space you left for it.
If you want a more specific setup, use manual partitioning but it doesn't sound like it.

---

### Post by DW1988 on 2012-08-20
> **darkod said:**
> DO NOT resize windows with the installer!!! :)

Boot windows, open Disk Management and shrink the windows partition for as much as you want to allocate to ubuntu. Leave the newly created space as unallocated, DO NOT create ntfs partition from windows.
Restart windows few times to acknowledge the shrink.

After that start the xubuntu installer (boot with the cd) and it should install automatically into the unallocated space you left for it.
If you want a more specific setup, use manual partitioning but it doesn't sound like it.

Have never used ubuntu  before (OpenSuse), so I assumed the new partition would be ext3/4. Hmmmm.... May stick with suse for my new laptop too as this has  reduced my confidence.

Additionally I have found :

[http://askubuntu.com/questions/110160/how-do-i-resize-partitions-using-the-simple-installation-wizard-installing-a-se](http://askubuntu.com/questions/110160/how-do-i-resize-partitions-using-the-simple-installation-wizard-installing-a-se)

which indicates the partition on left is the original.

---

### Post by darkod on 2012-08-20
Yeah, on the left should be the original.

The ubuntu partition will be ext4 and a swap partition. The installer will create them form the unallocated space.

The main reason not to resize windows using the ubuntu installer is because windows doesn't like that and sometimes (not always) can become unbootable wanting a chkdsk to be run first. But since you can't boot it to run chkdsk, you are in sort of catch 22.
That's why it's always better to shrink suing windows Disk Management, and install ubuntu into the unallocated space created.

I only said not to shrink it with the ubuntu installer, not sure what put you off from installing. I never said it's a bad idea to install. :)

---

### Post by hanketsu on 2012-08-20
I have a question now. I have an MSI GT60 laptop running a 750GB HDD and using a 128GB SSD as a caching drive in Windows 7 using the IRST. 

The most drive space IRST can use for caching is 64GB so it left me with a 50GB unallocated partition.

I am trying to install Ubuntu 12.04 on the 50GB partition on the SSD caching drive, but when I am installing it is not showing any partitions and it will not allow me to continue with the Linux installation. 

Any thoughts as to why it is not letting me use the 50GB of free space on my caching SSD?

---

### Post by darkod on 2012-08-20
> **hanketsu said:**
> I have a question now. I have an MSI GT60 laptop running a 750GB HDD and using a 128GB SSD as a caching drive in Windows 7 using the IRST. 

The most drive space IRST can use for caching is 64GB so it left me with a 50GB unallocated partition.

I am trying to install Ubuntu 12.04 on the 50GB partition on the SSD caching drive, but when I am installing it is not showing any partitions and it will not allow me to continue with the Linux installation. 

Any thoughts as to why it is not letting me use the 50GB of free space on my caching SSD?

Unfortunately I think IRST works in such a way that it marks the ssd as raid member, so the ubuntu installer will ignore it even if only part of the disk is used by IRST.

From what I have seen on this forum, you have to disable IRST and remove the raid meta data from the ssd in order to use it.

---

### Post by hanketsu on 2012-08-20
> **darkod said:**
> Unfortunately I think IRST works in such a way that it marks the ssd as raid member, so the ubuntu installer will ignore it even if only part of the disk is used by IRST.

From what I have seen on this forum, you have to disable IRST and remove the raid meta data from the ssd in order to use it.


Okay, thanks. That is what I was afraid of.

---

