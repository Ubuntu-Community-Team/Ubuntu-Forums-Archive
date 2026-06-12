---
title: "Can't install Xp Dual Boot"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by D. Pirate on 2008-11-20
I have a studio 15 from dell that shipped with Ubuntu 8.04. I now need to use Visual Studio for one of my classes, but I can't install Win Xp. I suspect that I need to properly partition my drive. The problem is that I don't know what to do to my drive. This is a screenshot of gparted for my hard drive. Is there anything wrong?

---

### Post by D. Pirate on 2008-11-20
I have a dell Studio 15 that shipped with ubuntu 8.04, but I can't install Win Xp for Visual Studio, which I need for class. I suspect that it is the partitioning on the hard drive. Here's a screen shot from gparted.

---

### Post by dmizer on 2008-11-20
Please do not create duplicate threads in multiple locations. It creates a big problem for people trying to help you and duplicates work for both you and the people trying to help you.

I've merged your threads and moved them to the installation forum.

---

### Post by Kinetic Being on 2008-11-20
Your partitions are really odd, I don't see the point to many of them...But I'm no master at this stuff...

I know I couldn't get Windows XP to install after Ubuntu, so I had to install windows, wiping the entire system, then install ubuntu which very neatly creates a dual-boot setup.

---

### Post by D. Pirate on 2008-11-20
> **Kinetic Being said:**
> Your partitions are really odd, I don't see the point to many of them...But I'm no master at this stuff...

I know I couldn't get Windows XP to install after Ubuntu, so I had to install windows, wiping the entire system, then install ubuntu which very neatly creates a dual-boot setup.

I don't know why the partitions are like that, but the problem is that the windows installation will freeze when it gets to the "Starting Windows" point. Then I get a blue screen. I think that the problem has something to do with the hard drive, but then again I am not sure.

---

### Post by Pumalite on 2008-11-20
What is sda6? If it's Windows; then you are trying to boot it from a logical partition. Better start again and install Windows in sda1 And next Ubuntu.

---

### Post by programmer8922 on 2008-11-20
I successfully installed XP as my second OS with this [tutorial]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm"). Also, with a slipstreamed install disc XP even named its install partition drive C, even though it wasn't installed on the first partition.

---

### Post by Kinetic Being on 2008-11-21
My best advice is to **backup** everything that is important you to onto a CD, then install windows, reformating the entire harddisk into a windows installation. After it is installed, install Ubuntu from the Live CD (not while still running windows [the wubi installer]) and Ubuntu should make the partitions like this:

sda0=windows partition, it should be ntfs not fat32/fat16
sda1=ubuntu partition, it should be ext3
sda2=linux-swap, should be twice the size of your RAM


This should all be the default setup in the ubuntu installer, so you shouldn't have to do anything. (the names may be different, but it should look similar to that)

---

