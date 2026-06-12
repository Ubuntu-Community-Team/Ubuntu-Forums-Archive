---
title: "Error while Installing Ubuntu 10.10"
date: 2010-11-25
forum: Installation &amp; Upgrades
---

### Post by JojAGT on 2010-11-25
I was trying to install ubuntu, and In the part to "Allocate drive Space" I selected to do it manually because the other option was to Erase the entire disk and I dont want to erase it all. I want to Dual boot win7 and ubuntu. So I have the main partition where is Windows and a secodary partition (51.2Gb) where I want to install ubuntu.  But when I select it, it gives me this error

"No root file system is defined

Please correct this from the partitioning menu."

This is how its partitioned my disk

sda1 (ntfs) 1.6Gb
sda2 (ntfs) 257.7Gb
sda3 (ntfs) 51.2 Gb
sda4 (ntfs) 9.6 Gb

What am I supposed to do?. I tried to format the disk and leave it free, tried to format the disk with ext4, tried to install ubuntu on the partition that windows made (ntfs).

Thanks a lot for reading. I read a whole guide of dual booting and windows booting. But couldnt find anything about this.

Just an other thing on EasyBCD guide for ubuntu  ( [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu) )  it saids that theres a bug on 10.04+ "requiring the user to first give control of the MBR to GRUB2, and then use EasyBCD to put the Windows bootloader back in control". Is it fixed in 10.10[U]?
[/U]

---

### Post by HeZ on 2010-11-25
Hi,
I am no expert so this answer may be wayyy off (in fact i just signed up to the forum cuz im stuck on the next step haha).
But I think what u need to do is select the partition you wish to install Ubuntu onto and click change, select the format as ext4 and in the box where it says mount location or something like that, enter a backslash.
Then that should be your root filesystem.

Hope that helps
HeZ

---

### Post by JojAGT on 2010-11-25
oooh... thanks for that I'll try it now! :)

---

### Post by sikander3786 on 2010-11-25
You need to define the mount points advised professionally by **HeZ** in his first post :P

Two partitions basically,

1. Ext3 or Ext4, Size > 8 GB (My Recommendation), Mount Point '/'

2. Swap, Size = RAM X 2

Regarding dual boot, if you have got only one HDD, let Grub install to its default location and it would be readily dual booting.

Open for further queries :-)

---

### Post by JojAGT on 2010-11-29
@sikander3786 Thanks for the info I could installed
defined the mount point = "/"

@HeZ Thanks man, followed your advice too :D

---

