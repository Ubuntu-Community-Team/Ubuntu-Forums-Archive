---
title: "Drive not in fstab"
date: 2012-04-20
forum: Installation &amp; Upgrades
---

### Post by NeonSamurai on 2012-04-20
Okay, brief background:

Threw out old server and built a new one using a Zotac Atom board to try and conserve energy, and as part of that decided to use an HP USB drive as the boot drive. Installed XBMCBuntu on it as the OS and to be honest it's all gone swimmingly. Very impressed with both the hardware and the software.

There is however one issue:

I've now added a 2TB SATA HDD to the server, but it doesn't always mount properly. Normally that's fixed with a couple of mouse clicks and away I go, but when I started looking into the problem I starting getting a bit confused. Here's what I get with fdisk -l:

> WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  3907029167  1953514583+  ee  GPT

Disk /dev/sdb: 16.1 GB, 16072572928 bytes
255 heads, 63 sectors/track, 1954 cylinders, total 31391744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000dd84

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    27219967    13608960   83  Linux
/dev/sdb2        27222014    31389695     2083841    5  Extended
/dev/sdb5        27222016    31389695     2083840   82  Linux swap / Solaris


So for some reason the system has decided that the new drive is sda1 and the USB boot drive is sdb1. I presume that this is because the former is SATA. No problem, as the system boots fine.

Now here's fstab:

> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=51c6deb7-c649-49b5-a8d7-14229bae8314 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0f44a2a7-5171-4eb7-825c-fd1d338b1177 none            swap    sw              0       0

It worryingly has errors and no mention of the 2TB SATA. Fair enough, it wasn't connected when I built the system. So I called up a blkid and got this:

> /dev/sda1: LABEL="Vault2" UUID="a4f43c54-aab7-44f8-8d6e-ab94799fbdd6" TYPE="ext4"
/dev/sdb1: UUID="51c6deb7-c649-49b5-a8d7-14229bae8314" TYPE="ext4"
/dev/sdb5: UUID="0f44a2a7-5171-4eb7-825c-fd1d338b1177" TYPE="swap"


So my questions are as follows:

Can I simply add the 2TB SATA drive in fstab using this line:

> UUID=a4f43c54-aab7-44f8-8d6e-ab94799fbdd6 /media/Vault2  ext4 0 0 0

and is the 

> UUID=51c6deb7-c649-49b5-a8d7-14229bae8314 /               ext4    **errors=remount-ro **0       1


anything to worry about?

Thanks


Mark

---

### Post by darkod on 2012-04-20
Yes, you can add the SATA disk with that line. What I have seen for mounting is something like:
UUID=XXXXX /mount_point ext4 defaults 0 0

Instead of the 0 0 0 you have at the end of your command. But that doesn't mean yours is wrong.

And for the errors=remount-ro, that is a normal option for the / partition so I think you have nothing to worry about.

PS. If the Vault2 folder doesn't exist in /media you will have to create it first so that the pount point /media/Vault2 can work.

---

### Post by NeonSamurai on 2012-04-20
Thanks Darko,

I went with:

UUID=XXXXX /media/Vault2 ext4 defaults 0 1

Just rebooted a few times and my SATA HDD is appearing as required. 

And you're right about creating the Vault2 folder, I'd already set that up but it is necessary. 

Thanks for the help and your quick response.


Mark

---

