---
title: "newbie install/update question"
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by amcusack on 2010-11-24
I have a laptop which has both windows 7 64 bit & ubuntu 10.04 installed.

At boot time, the grub menu comes up & I can select to boot windows or Ubuntu.

That works fine.

I now want to replace the ubuntu 10.04 with 10.10 64 bit

here is what Gparted shows for my disk allocation
 

```

/dev/sda1 ntfs system reserved   100MiB 33.59MiB 66.41MiB(flags boot)
/dev/sda2 ntfs                 97.56GiB 29.02GiB 68.54GiB
/dev/sda3 extended             51.39GiB
/dev/sda5 ext4                 49.25GiB  5.11GiB 44.14GiB
/dev/sda6 linux-swap            2.14GiB

```

I have the iso for Ubuntu 64 bit

I got to the allocate drive space, i assume i need to specify partitions manually ?

if so, the next screen asks device for boot loader installation - is that dev/sda1 ?

then the only button on the screen is install now - how will the installation know that i want to replace the previous version or will there be more questions later on ?

sorry to be a total newb  :confused:

---

### Post by sikander3786 on 2010-11-25
Welcome to the forums :-)

If your 10.04 install is working, you can do a live upgrade from the internet using System > Administration > Update Manager.

> 
I got to the allocate drive space, i assume i need to specify partitions manually ?

If you want a clean install, specify partitions manually. Select the same partitions Ubuntu is on previously and select them for a format. Tick the small box for format just in front of those partitions. Simple.

But make sure you don't mark any other partitions for format accidentally or you'll lose anything on them obviously. The only partition you need to format here is the one labeled '/',

> if so, the next screen asks device for boot loader installation - is that dev/sda1 ?

It needs to be sda, not sda1 if you've got a single HDD. It can be installed to sdb, sdc if you've got multiple HDDs but make sure your Bios is capable of booting from other HDDs.

For the sake of simplicity, I'll advise to install it to sda here.

> then the only button on the screen is install now - how will the installation know that i want to replace the previous version or will there be more questions later on ?

Format and it would know that it is going to be a clean install :P

Good Luck!

---

