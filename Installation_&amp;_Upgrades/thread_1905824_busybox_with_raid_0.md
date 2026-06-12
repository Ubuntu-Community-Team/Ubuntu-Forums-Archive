---
title: "busybox with raid 0"
date: 2012-01-07
forum: Installation &amp; Upgrades
---

### Post by Bray90820 on 2012-01-07
i am trying to install ubuntu 11.10 x64 desktop with raid 0 every time i do the installation finishes properly but then i try  to boot and it boots into busybox

---

### Post by darkod on 2012-01-07
Are you using the standard desktop cd or the alternate install cd?

---

### Post by Bray90820 on 2012-01-07
first i tried the alternate cd then i tried the regular one sand thing happend both times

---

### Post by darkod on 2012-01-07
I forgot to ask the first time sorry, is this bios raid (fakeraid) or software raid?

Softraid doesn't work in raid0 unless you have separate /boot partition outside the array. Even with fakeraid I think this can be the issue. In raid0 files are split on the disks and I'm not sure the boot files like that.

Regardless whether you use fakeraid or softraid, try this:
Use the alternate cd to install, it has raid support.
Create 200MB raid1 device for /boot.
Create the rest as raid0 device for root.

Towards the end of the install watch out whether the bootloader (grub2) gets installed successfully. I think the problem is that the bootloader isn't installed OK.

If you don't wanna try another setup, we can check of grub2 is installed but I would try the setup with raid1 for /boot first.

---

### Post by Bray90820 on 2012-01-07
i think it's soft raid i configured it with my motherboards bios

---

### Post by darkod on 2012-01-07
No, software raid is referred to a raid configured with the ubuntu OS.
The bios raid is fakeraid because in a way it is software raid and not dedicated hardware raid. But to make the distinction, it's not the same as softraid with the linux OS.

When asked where you want to install the bootloader, did you select the /dev/mapper device and not a particular disk (sda, sdb)? You need to install it on the raid device.

I would still try the suggestion from my previous post about the /boot device.

---

### Post by Bray90820 on 2012-01-07
i just did the default ubuntu gave me

if i were to use a pci raid card would it work

---

### Post by darkod on 2012-01-07
OK, post the output of:
sudo fdisk -l (small L)

---

### Post by Bray90820 on 2012-01-07
can i do that with the live cd

---

### Post by darkod on 2012-01-07
Sure. Just open terminal, issue the command and post the ouput. It's best to include the result in code tags, or select the text and hit the # button in the toolbar above when writing the post.

---

### Post by Bray90820 on 2012-01-07
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/mapper/nvidia_daiedbda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/mapper/nvidia_daiedbda: 3000.6 GB, 3000603817984 bytes
255 heads, 63 sectors/track, 364802 cylinders, total 5860554332 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_daiedbda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.
ubuntu@ubuntu:~$ 

```

---

### Post by darkod on 2012-01-07
You are configuring raid0 with 1TB and 2TB disks? You are aware that you will only be able to use 2 x 1TB and not the total 3TB?

raid0 array is created from two same size disks, or it uses the part of the larger disk equivalent to the smaller disk.

Except this, /dev/sda doesn't seem to have a partition table. You can create one with parted, also from live mode. It would go like:
sudo parted /dev/sda
mklabel gpt
exit

That will create new gpt partition table. It will also delete any data on the disk but I assume you have no data there since you are still installing.

---

### Post by darkod on 2012-01-07
Unfortunately it's very late in my time zone so I have to leave you now. :)

We can continue tomorrow if you don't sort it out by then.

Think about your raid setup and how you want to plan it. With disks of different size creating a raid0 fakeraid is wasting space on the larger disk.

---

### Post by Bray90820 on 2012-01-07
then i am not using raid 0 what i am using is spanning which i thought was raid 0

---

### Post by Bray90820 on 2012-01-08
i found out i wasn't using raid at all i was using a form of combining 2 different sized drives together to make 1 called spanning

---

### Post by darkod on 2012-01-08
In that case I'm not sure if this setup can work with ubuntu at all. Have in mind that some motherboard options are designed primarily for windows and not taking linux into account.

If your plan is to combine the two disks into one single 3TB space, I would suggest LVM. It's not as complicated as it might sound.
Basic info: [http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29](http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29)

If you want raid protection of your data in case one disk fails, you can also plan something like this with ubuntu software raid:
raid1 array of the 1TB disk and 1TB partition on the 2TB disk
using the second half of the 2TB disk as storage which is not raided

The data on the 1TB raid1 will be protected against failure, and the data on the 1TB partition on the larger disk not. But at least it gives you some protection. But in this case the usable space will be only 2TB in total, not 3TB.

It all depends how you want to use your computer. But you are planning to put 3TB data on there without any kind of protection against disk failure?

---

