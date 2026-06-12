---
title: "Ubuntu 11.04 installer can't find HDD"
date: 2011-10-12
forum: Installation &amp; Upgrades
---

### Post by pitje06 on 2011-10-12
Hi all, I'm new to this forum, and hoping someone is able to help me.
I'm trying to install Ubuntu 11.04 to a 80GB HDD (IDE Master) from a CD, but the installer will not find it. On the second HDD (250GB IDE slave) a functional Debian installation (with Grub) is present. I would like to preserve this installation until I am sure Ubuntu is up and running.
Ubuntu live will boot just fine, and GParted can find and format the disk in question (Ill call it sda from now on), but the installer wont. The installer does, however give me the option to select sda as the device for boot loader installation (Device for boot loader installation: /dev/sda), but I can't install ubuntu to the disk (or format it from the installer).
lshw states I have a Pentium 4 2.8GHz processor with 512MB RAM.

I'm now going to try and disconnect the 250GB disk before trying again, but any help will be very much appreciated.

---

### Post by Basher101 on 2011-10-12
I really do not know why gparted wont list it...i know alot about partitioning, shared partitions of Windows and Linux but here, i have no clue...

---

### Post by pitje06 on 2011-10-12
Thanks for your reply.

As stated GParted can find and format the disk, but the installer can find it.

---

### Post by pitje06 on 2011-10-12
Ok, latest update.
I disconnected the 250GB hdd, but the installer still cant install to sda.

Please help.

---

### Post by pitje06 on 2011-10-12
Back again for the latest update, I've given up on Ubuntu and am now happily installing Debian, which found my HDD without any issues whatsoever. 
I think I'll steer clear from Ubuntu for quite some time. 

Thanks for your time.

PS. for the record, it is a WD800 (WD800BB-00CAA1)

---

### Post by Rubi1200 on 2011-10-12
Glad you found a solution, but sorry you didn't stick with Ubuntu.

There could be a number of reasons why the installer failed and we would have hopefully found a way to figure it out.

For example, do you have RAID, a GPT disk, or some other unusual setup?

---

### Post by pitje06 on 2011-10-14
No, none of the above. It is a simple 80GB disk (bit old, but ok). I also tried installing with the BIOS IDE setting to compatible, and I also tried the bootflags noacpi and acpi=off. Before trying to install Ubuntu to the disk it used to house a Windows installation, which I removed by deleting the partitions.
If more information is needed to resolve this issue in future versions, I'll be happy to supply what I can remember.

---

