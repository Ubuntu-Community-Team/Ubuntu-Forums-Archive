---
title: "Noob needs help with partitions..."
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by lestrade on 2008-05-25
So, I get a brand spanking new laptop (Toshiba P305S8825) with a 300 gig hd.
I use gparted livecd to shrink the vista partition down to about 60 gigs.
I then tried to set up partitions for swap and root (/).  I think my problem is that...well, it doesn't matter what I think. I am a bit confused.
Both Ubuntu and Vista will boot. However, I did not set a /home partition....
Here is the result of fdisk -l. Any help would be appreciated.
JPL
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbfbfbfbf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         193        7936    62203680    7  HPFS/NTFS
/dev/sda3            7937        9795    14932417+  82  Linux swap / Solaris
/dev/sda4            9796       15874    48829567+  83  Linux

Disk /dev/sdb: 1048 MB, 1048576000 bytes
255 heads, 63 sectors/track, 127 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         128     1023968+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(126, 254, 63) logical=(127, 122, 59)

---

### Post by iaculallad on 2008-05-25
You could try this [guide]("http://www.psychocats.net/ubuntu/separatehome").

---

### Post by lestrade on 2008-05-25
Thanks, guy.  I printed it out and will read it tonight.
PL

---

### Post by molotov00 on 2008-05-25
There is ONE thing you said that confused me and I'd like to clarify. You do not need /home to be its own partition. 

In fact, in most situations it isn't. On my install there's the main partition and one for swap files. If you can log in without errors then maybe your /home directory is working just fine? 

If not... you can just create a /home directory (sudo mkdir /home) and use the command "usermod" to set your home directory. i.e. for me: 

sudo usermod molotov --home=/home/molotov 

will set my home directory to /home/molotov.

M

---

### Post by lestrade on 2008-05-26
ah! Thanks!
I was waiting for a response, so yours has saved me.
JP

---

