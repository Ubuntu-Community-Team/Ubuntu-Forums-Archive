---
title: "Won't boot, upgraded 12.04 to 14.04, possibly deleted Windows 8 partition"
date: 2015-02-02
forum: Installation &amp; Upgrades
---

### Post by theincubus313 on 2015-02-02
So I think I have dug myself into an irreparable hole, but it would be nice if those more wise than I could help confirm that and/or save my computer.

I have a Lenovo ThinkCentre K430 that was merrily dual booted with Windows 8 and Ubuntu 12.04.2LTS. I tried to upgrade it while in Ubuntu side to 14.04LTS. The upgrade failed a few times, and after searching for the package that was blocking the update for a while to no avail, I created a bootable live USB for 14.04. I booted to "Install Ubuntu", assuming correctly that there would be a "Replace 12.04 with 14.04" option. It came with a warning that this would delete my Ubuntu data, which I was fine with as I had backed it all up. However, after doing this and doing a prophylactic booting again to my live USB to run boot-repair (I have never *not* needed boot-repair on a dual boot, a feeling I'm sure many are familiar with...), I tried booting without the USB and I get the BIOS error:

"Error 1962: No operating system found"

I have done a large amount of Googling of this issue and found that, for others, the error could hav been in:

1) faulty SATA cables (which of course it is not as my system was running perfectly before this with Windows and Ubuntu 12.04)
2) Compatibility Support Module (CSM) not enabled: This is a, as far as I can tell, Lenovo-specific option that I, and most posters, are not entirely sure what it does, but as far as we can tell it allows for partitions of different formats to play nice on a Lenovo system. this did not work
3) pointing to the wrong partition for boot. Tried a few solutions to this to no avail similar to [here]("http://ubuntuforums.org/showthread.php?t=2243715&page=2") and [here]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1302939")

however, I noticed something when playing around with gparted: I suddenly ad only 3 partitions, not the seven-ish i am used to seeing on the dual boot. I realized that, as far as gparted and fdisk -l was concerned, my Windows partition (not as recently backed up) was not recognized as being there!! At this point I diverged from experience and freaked out more than I should have and, in an attempt to get my windows partition back, ran (on the advice of someone who didn't really know what he was talking about:

sudo fdisk /dev/sda

Option: t
partition #: 1
Hex code: 83
option: w

which basically F*$%ed up my GPT so that my original Boot-Repair dump has changed to [this]("http://paste.ubuntu.com/10017263/").

output of ```
sudo fdisk -l
``` is 

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x28901239

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  3907029167  1953514583+  83  Linux
Partition 1 does not start on physical sector boundary.

Disk /dev/sdd: 8166 MB, 8166703104 bytes
224 heads, 63 sectors/track, 1130 cylinders, total 15950592 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          56    15950591     7975268    c  W95 FAT32 (LBA)


```

So now, as far as I can tell I have, in a night:

1) Failed to successfully upgrade to 14.04
2) nuked my 12.04 AND Windows 8.1 OSs
3) pissed off my BIOS
4) pooped on what was left of my partitions using fdisk like a n00b

If you or anyone you know can help with any of these problems, please let me know. I have not yet restarted my system since the fdisk stuff, so those changes, as far as I know, have not taken effect yet. I will not restart my system until I hear advice that says I should or enough days pass where I will consider myself defeated without help and I will just start rebuilding from scratch (that indeed will be a sad day  :mad: )

---

### Post by ubfan1 on 2015-02-02
Sadly, looks like bug 1265192.  Add yourself to the bug list.  Hope your backups are in good shape for the rebuild.

---

### Post by theincubus313 on 2015-02-03
Woof. Ok, think I should start from scratch with the windows build and delete what i have (or don't really have) from 14.04, or should I try to make this ubuntu work before i reinstall windows

---

### Post by ubfan1 on 2015-02-03
I think it's better to install Ubuntu after Windows.  That's the standard way installs are done, and most documentation assumes that.  Also, you should wind up with a working grub after the Ubuntu install which should work for both Windows and Ubuntu.

---

