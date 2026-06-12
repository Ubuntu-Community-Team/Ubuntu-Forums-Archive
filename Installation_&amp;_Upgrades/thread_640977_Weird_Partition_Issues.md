---
title: "Weird Partition Issues"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by dnowell on 2007-12-14
I installed Ubuntu 7.10 on a Dell Vostro 1500 for my wife about 3 weeks ago and it's been working great.  Just yesterday though she started getting Grub error 17 when booting up.  This isn't a dual-boot system, so it doesn't give us the option to go into Grub or anything like that.

First I tried using some Live CDs to check gparted, but it just claims that the 160 GB hard drive is unallocated.  Knoppix saw the little partition Dell automatically sets up to put some Windows software but nothing else.

I found the Linux Rescue Disk and tried that out.  With testdisk I can see my big hard drive, and it even sees partitions, but this is what it shows:
  Partition                       Start    End         Size in sectors
1 * Linux                         0 1 1 18703 254 63 300479697
2 E extended LBA   18704 0 1 19456 254 63  12096945
5 L Linux Swap        18704 1 1 19456 254 63  12096882

When I tell it to proceed in the Analyse partitions menu, it then shows this, but it doesn't seem to do anything.
  Partition                       Start    End         Size in sectors
* Linux                         0 1 1 18703 254 63 300479697
L Linux Swap        18704 1 1 19456 254 63  12096882

At first I thought that would set it right, so I went through the menu and then told testdisk to write to the master boot record.  So now it shows the 1234F: on boot, and 1,3 & 4 don't do anything.  2 just hangs.

Anyone have any ideas what might have happened and how I can fix it?  I put in a lot of time getting the drivers set up correctly with this laptop and really don't want to do it all over again.  Thanks!

---

### Post by dnowell on 2007-12-16
If I were to try and do a new install of another OS like Red Hat or Windows, is there any way that would help, or would it just wipe out what's already there?

---

### Post by briandu on 2007-12-16
Hi there

boot up with the 7.10 live disk.

Run grub and checkout the partitions

if look OK then open terminal 

run grub-install /dev/sda1  #or /dev/hda1 - whichever the hard disk is seen as.

reboot

---

### Post by dnowell on 2007-12-16
I can see the partitions using Gnome Partition Editor, and /dev/sda1 is the big partition.  When I run grub-install /dev/sda1 I just get this:
Could not find device for /boot: Not found or not a block device.

---

### Post by Partyboi2 on 2007-12-16
have a look at herman's grub page.You will find troubleshooting for grub error 17. It might help, or atleast give you some ideas on where to go from there.
[http://users.bigpond.net.au/hermanzone/p15.htm#When_trying_to_boot_Linux](http://users.bigpond.net.au/hermanzone/p15.htm#When_trying_to_boot_Linux)

---

### Post by dnowell on 2007-12-17
That page did the trick.  Specifically, the part about mounting my "dead" drive:
sudo mount -t ext3 /dev/sda1 /media/ubuntu 
Once I was able to access it, a fresh grub install wrote a good MBR.
Thanks for your help!

---

