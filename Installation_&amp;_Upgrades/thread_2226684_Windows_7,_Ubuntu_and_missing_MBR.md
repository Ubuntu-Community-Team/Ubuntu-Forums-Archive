---
title: "Windows 7, Ubuntu and missing MBR"
date: 2014-05-28
forum: Installation &amp; Upgrades
---

### Post by rex27 on 2014-05-28
Hi,

Here's my story:

I had Ubuntu installed on my Thinkpad L430 via Wubi on Windows 7. 

I wanted to move Wubi to its own partition so I used the migration tool, everything went swimmingly. Grub was now the bootloader.

I saw that I now had 170 GB of unallocated space on my disk, in between the Windows and Ubuntu partitions. 

I decided to make some of this into swap space, and to merge some of this into the Ubuntu partition.

Grub wouldn't let me do this because I would have more than 4 primary partitions on my disk (including the Lenovo recovery disk etc.)

So I decided to try to use the Windows partition editor to solve this. Booted into Windows, made the unallocated space my E drive. 

I tried to reboot but now my hard disk won't mount. I think the master boot partition has been overwritten.

Additionally, the ext4 partition with the newly migrated Ubuntu filesystem has grown larger and absorbed partitions at the end of my hard disk.

Any idea what I can do to get anything back? 

The attachments are screenshots taken using an Ubuntu Live-disk.
[ATTACH=CONFIG]253545[/ATTACH]

[ATTACH=CONFIG]253548[/ATTACH]

---

### Post by bcbc on 2014-05-28
Why did you think Windows could create more than 4 primary partitions? Windows just converted your drive to 'dynamic' partitions (type SFS) and this means it stores information about the partitions that are not present in the partition table (not visible to linux).

I'd guess that installing a Windows bootloader will at least get Windows booting. (from windows repair command prompt: bootrec /fixmbr)
But to get back to what you had you will need a partitioning tool (like easeus) to reverse the drive from dynamic back to normal.

---

### Post by rex27 on 2014-05-28
First, thanks for replying.

> Why did you think Windows could create more than 4 primary partitions?

- Because I'm an idiot.

bootrec/fixmbr resulted in me getting "Missing operating system" as an error. 

Is there a free equivalent to EaseU that gives me the tools to do what you suggest?

---

### Post by paul142 on 2014-05-28
Look up Hiren's Boot CD, its got lots of tools and its free.

---

### Post by bcbc on 2014-05-28
In the gparted picture, the boot flag is on /dev/sda1, but on the fdisk output it is on /dev/sda4 the 'Linux partition'. For windows to work it has to be on the windows boot partition, the one that contains bootmgr and /boot/BCD. 

Fix that and it will probably stop saying 'missing operating system'

---

### Post by rex27 on 2014-05-28
Thanks bcbc - I managed to get the wubi version of Ubuntu back. Unfortunately, Windows crashes on booting. 
Do you reckon it's still the same problem - i.e. dynamic instead of normal/basic?

---

### Post by bcbc on 2014-05-28
Windows shouldn't crash - it should know how to handle the dynamic disk. But the whole thing with it 'expanding' /dev/sda4 which wasn't ntfs in the first place might indicate that Windows lost the plot somewhere. 

As to whether switching from dynamic will fix Windows - hard to say without more info on how/why it is crashing. But now might be a good time to mount and copy your important data to an external drive, so that if your fixes don't work, at least they won't further compromise your data.

---

### Post by paul142 on 2014-05-29
> **rex27 said:**
> First, thanks for replying.



- Because I'm an idiot.

bootrec/fixmbr resulted in me getting "Missing operating system" as an error. 

Is there a free equivalent to EaseU that gives me the tools to do what you suggest?

Dont label yourself an idiot, this isnt easy stuff. Ask questions and learn!

---

### Post by rex27 on 2014-05-29
Hi again,

So I realize that this is veering towards a Windows thread now, but I'm now getting the 0x7b error when Windows tries to boot. Running bootrec/fixboot tells me that there are no recognized filesystems around. 

Any ideas?

---

### Post by rex27 on 2014-05-29
I've run testdisk again and this is what I get (see attached). 

I'm not sure what to do about the 'merged' partitions. 

Thanks for all your help, I'll try and update this thread when I find a solution.

[ATTACH=CONFIG]253570[/ATTACH]

[ATTACH=CONFIG]253573[/ATTACH]

---

### Post by rex27 on 2014-06-03
Okay, I think I got Windows back now as well. The notes are for future reference:

Basically in the last testdisk image above, I worked out which of the partitions corresponded to the ones I had before and restored them. (I cross-referenced the partitions testdisk found with its quick search and its deeper search.) Crucial for Windows was the "Lenovo_Recovery" partition. I made sure that there were only 4 primary partitions this time, and reverted back to Wubi for the time being. 

The 4 are:
- SYSTEM_DRV
- Windows_OS
- One of the Linux partitions, which had my wubi-migrated Ubuntu installation
- Lenovo_Recovery

The old Ubuntu partition doesn't boot, but I'm just going to reformat it, enlarge it to include the un-allocated space I started off with, and re-migrate Ubuntu from Wubi to this.

Thanks again for your help bcbc, and for everyone else's comments as well.
old Ubuntu partition, which I also recovered,

---

### Post by bcbc on 2014-06-06
Glad you figured it out. Those initial testdisk screenshots looked unpromising at first.

If you replace the linux partition with an Extended (primary) partition, you'll have more flexibility - you can create logical partitions for Ubuntu and also a swap partition (to enable hibernation), or possibly create additional partitions for a separate /home or for shared data. Even if you just use the full space for a single partition,  it's still a good idea to make it an extended with a logical, because then if you need to you can shrink it and add more partitions later. If it's a primary partition you'd need to delete it to do the same (I think there are some partitioning tools that can convert Primary to Extended + logical as well).

---

