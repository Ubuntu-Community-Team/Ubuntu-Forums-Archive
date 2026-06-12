---
title: "Need to know how to install Ubuntu with Vista"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by CHUNKYBOWSER on 2008-05-04
Pretty general question... I am currently running Windows Vista, but I want to be able to run Ubuntu without losing anything on Vista. xD Are there any videos that might show me how?

---

### Post by RATM_Owns on 2008-05-04
Under Control Panel look for Disk Management and shrink your Vista partition at least 4 GB.
Then when it's done, put the live CD in, reboot and go along the installation as you normally would. Then after the Partitioner is set up, choose "Largest Continuous Free Space" and continue normally.

---

### Post by Pumalite on 2008-05-04
This might help:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)

---

### Post by CHUNKYBOWSER on 2008-05-04
Would it be OK to make a partition of about 30 GB for Ubuntu instead?

---

### Post by DBrocks on 2008-05-04
Here's a better idea: Wipe vista. You don't need all that pricey software and virii anyway :lolflag:. 


Just kidding.  :guitar:

---

### Post by DBrocks on 2008-05-04
> **CHUNKYBOWSER said:**
> Would it be OK to make a partition of about 30 GB for Ubuntu instead?

Yes, that would work too.

30gigs is all Ubuntu really needs.

---

### Post by CHUNKYBOWSER on 2008-05-04
OK, so I'm going to write Ubuntu 8.04 to a CD... Then restart the computer and boot from the CD, correct? After I install everything, how would I get back to Windows? :p I'm kind of a noob at this stuff.

---

### Post by Pumalite on 2008-05-04
Dual boot for a while and when you know what you like; act accordingly.

---

### Post by DBrocks on 2008-05-04
> **CHUNKYBOWSER said:**
> OK, so I'm going to write Ubuntu 8.04 to a CD... Then restart the computer and boot from the CD, correct? After I install everything, how would I get back to Windows? :p I'm kind of a noob at this stuff.

After it installs, it will install GRUB (a boot loader) automatically. When it boots, just select "windows".

---

### Post by CHUNKYBOWSER on 2008-05-04
Cool. :) And there is no real danger to my files on Windows, correct?

---

### Post by c007c on 2008-05-04
I'm doing that now. All I had to do was create unallocated space by shrinking my windows Vista filesystem and delete the volume info. Then load the Live CD, and during the install you can either choose use all the unallocated space, or partition the unallocated space yourself manually. The only way you would blow things away is choosing entire disk option, which may be the default!

Then after the install you will see a grub loader screen during the boot sequence, where you can choose to boot Vista or Ubuntu. By default, Vista (Longhorn) will be last. You will have to edit the menu.lst file, to make Vista first (above automagic section). Remember, if you decide to remove Linux after you do this, you won't be able to get past grub. Grub needs to be removed prior to removing Linux, via repair of master boot record, something you need to ask somebody that went back to windows how to do. I have an idea of what the command is, but would never do it.:)

---

### Post by DBrocks on 2008-05-04
There shouldn't be. But, you may want to back up your important files. You can never be too safe. I have never had Ubuntu screw up windows, and it is very rare, but could happen

---

### Post by CHUNKYBOWSER on 2008-05-04
Oh, one more question. What type of partition should I make? FAT32 or NTFS?

---

### Post by DBrocks on 2008-05-04
> **c007c said:**
> I'm doing that now. All I had to do was create unallocated space by shrinking my windows Vista filesystem and delete the volume info. Then load the Live CD, and during the install you can either choose use all the unallocated space, or partition the unallocated space yourself manually. The only way you would blow things away is choosing entire disk option, which may be the default!

Then after the install you will see a grub loader screen during the boot sequence, where you can choose to boot Vista or Ubuntu. By default, Vista (Longhorn) will be last. You will have to edit the menu.lst file, to make Vista first (above automagic section). Remember, if you decide to remove Linux after you do this, you won't be able to get past grub. Grub needs to be removed prior to removing Linux, via repair of master boot record, something you need to ask somebody that went back to windows how to do. I have an idea of what the command is, but would never do it.:)

To fix the MBR, find your windows boot disk, and boot into the recovery terminal. Then type "FIXMBR", and restart. NO GRUB! :lolflag:

---

### Post by DBrocks on 2008-05-04
> **CHUNKYBOWSER said:**
> Oh, one more question. What type of partition should I make? FAT32 or NTFS?

Doesn't matter. Ubuntu will format it to its own filesystem (ext3, far superior to NTFS). But, just go with NTFS, because I have installed on an NTFS drive before.

---

### Post by c007c on 2008-05-04
> **CHUNKYBOWSER said:**
> Oh, one more question. What type of partition should I make? FAT32 or NTFS?

Thats Windows stuff...Leave the partition unallocated. The install will create it for you (ext3)

---

### Post by DBrocks on 2008-05-04
> **c007c said:**
> Thats Windows stuff...Leave the partition unallocated. The install will create it for you (ext3)

That works too. Go with his idea. Formatting is a waste of time xD

---

### Post by c007c on 2008-05-04
> **DBrocks said:**
> To fix the MBR, find your windows boot disk, and boot into the recovery terminal. Then type "FIXMBR", and restart. NO GRUB! :lolflag:
What if you don't have one? What would you/could you do prior to wiping out Ubuntu, isn't there a "fdisk /mbr" command?

---

### Post by DBrocks on 2008-05-04
> **c007c said:**
> What if you don't have one? What would you/could you do prior to wiping out Ubuntu, isn't there a "fdisk /mbr" command?

You can't do fdisk in windows. (just tried) sorry, windows can't make anything easy. However, check out this site: It may help you

[http://www.softwaretipsandtricks.com/forum/windows-xp/27414-repair-mbr-without-xp-cd.html](http://www.softwaretipsandtricks.com/forum/windows-xp/27414-repair-mbr-without-xp-cd.html)

---

### Post by Pumalite on 2008-05-04
Super Grub will fix your Windows MBR:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

