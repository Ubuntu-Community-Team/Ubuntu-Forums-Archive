---
title: "Ubuntu/Win7 dual-boot on multiple disks?"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by EricJonsson on 2010-04-11
Greetings, all. I've got some problems related to setting up a dual-boot system between Windows 7 and Ubuntu. The related Wiki pages doesn't seem to adress the problem, and so I come here for help.
 
The thing is, I've got two hard drives involved:
 
- Disk 0 (SATA2), 400gb
- Disk 1 (SATA1), 250gb
 
I'd like to place Ubuntu on Disk 1, and Windows on Disk 0. None of the guides and tutorials I've read seems takes multiple drives into account.
 
Now, conventional wisdom says to install Windows first and Ubuntu second, since Windows will happily overwrite MBR with its own boot loader. At this time I've installed Windows 7, and notes that it has indeed created a NTFS partition on the larger 400gb disk, but also a smaller 100mb partition (!) on the other 250gb drive.
 
When I shortly thereafter install Ubuntu (9.10/10.04 desktop, AMD64) and click my way through to the partitioning screen, I'm presented with several options, and I find none of them making much sense:
 
- The "Choose between Windows and Ubuntu" option insists on installing Ubuntu on the same drive as Windows, and I can't seem to change this. In addition, even with this option chosen the system boots immediately into Windows when started.
- The "Clear everything on drive X and install Ubuntu" option removes the small 100mb partition that Windows installed, and thereafter I can't seem to recover Windows anymore.
- The "Install Ubuntu on largest free area" selects the right drive, but doesn't recognize Windows anywhere and so I am not given any OS options from GRUB at boot.
 
I'm kind of stuck now, so.. Any suggestions?

---

### Post by tom4everitt on 2010-04-11
Idiotic of windows to spread itself out on several hard drives :) It won't be a problem though, as long as you don't remove any hard drives or switch their places or something like that. 

Now, I think you have to choose manual option in the ubuntu installer. Create a an ext4 partition for ubuntu(mount point: '/'), and a small swap ~2gb, on the (mostly) free hard drive.

Just don't remove or change the windows partitions.

Also let it install its boot loader to (hd0), which is predefined I think.

---

### Post by EricJonsson on 2010-04-11
I seem to (finally) have found a solution. Windows insists on having the hidden mini-partition installed on the first harddrive, so by making the larger 400gb drive the first one in BIOS I managed to contain the Windows installation to that drive.

Then I installed Ubuntu as normal, creating a swap- and ext4-partition manually on the 250gb drive. GRUB was installed to hd0.

When the system restarted, it booted into Windows immediately. This issue was solved by simply switching back the 250gb drive (with Ubuntu) to be the first one in BIOS. Upon boot, the GRUB menu presented itself and offered the option between Ubuntu, Memtest86+ and Windows. Success!

I'll make sure to document this somewhere, I'm bound to run into the same moronic problem the next time I setup a dual-boot system like this...

---

### Post by tom4everitt on 2010-04-11
Great! Yeah, as the rule says:

ALWAYS INSTALL WINDOWS FIRST, AND INSTALL IT ON THE FIRST HARD DRIVE

And I guess with a little fiddling in bios, you can achieve almost any setup without breaking the rule :)

---

