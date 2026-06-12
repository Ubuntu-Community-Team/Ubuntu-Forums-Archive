---
title: "Partition Question"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by Hobbes1020 on 2008-05-29
I'm a complete noob when it comes to Linux and was wondering how I should configure the partitions for an Ubuntu 8.04 install. I'll be running it on an old 533 MHz Centrino laptop with 60GB of hard drive space and 1GB of RAM. Any help is greatly appreciated.

---

### Post by wdaniels on 2008-05-29
If you don't have any unusual requirements, then I can't think of any reason not to just go with the defaults - one ext3 partition for root system + home data and one swap partition for virtual memory. There's an option in the installation called "guided partitioning" (or something similar) that you can use.

Some people (like me) prefer to have a separate home partition, but unless you anticipate wanting to boot multiple systems in future I wouldn't worry about any of that since you still have the possibility to resize/move partitions etc. after the event anyway.

---

### Post by iaculallad on 2008-05-29
> **Hobbes1020 said:**
> I'm a complete noob when it comes to Linux and was wondering how I should configure the partitions for an Ubuntu 8.04 install. I'll be running it on an old 533 MHz Centrino laptop with 60GB of hard drive space and 1GB of RAM. Any help is greatly appreciated.

The typical partition scheme (given your 60GB HDD) for common computing would be:

the "root" partition (/ = 5Gb Ext3FS)
the "home" partition (/home = Remaining space in your 60GB drive)
the virtual RAM or "swap" (swap = 1Gb)

In any way, you could include your /boot, /tmp, /var, /usr directories.

---

### Post by Rallg on 2008-05-29
You didn't mention whether you will also have another operating system (such as Windows).

Before you install Ubuntu (or any Linux) be sure that your computer hardware can run it properly. Run the live CD, and be sure that you are reasonably satisfied with display, wireless, and any must-have peripherals. It will probably all work OK.

---

### Post by wpshooter on 2008-05-29
Assuming you are going to have only Ubuntu on this machine and that you are going to choose MANUAL partitioning method.

My recommendation would be to partition as follows:

/ = root - make it 15gb - if you are using the ALTERNATE install make sure you make it bootable

/home = home (data, storage, etc.) - make it the balance of your drive space after alloting maybe 1 or 2 gb for SWAP partition

/SWAP = SWAP - make 1 or 2gb.

Good luck.

---

### Post by Hobbes1020 on 2008-05-29
Great. Thanks for the info! :)

---

