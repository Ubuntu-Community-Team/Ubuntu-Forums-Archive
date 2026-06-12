---
title: "Not booting"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by timoross on 2010-04-09
I have an aspire one with an 8 gig ssd. 

The first time I tried to install UNR 9.10 Ubuntu could not format the drive. Now I have discovered that if I format the drive with gparted and leave the first 8mb unformatted I can assign the rest of the disk a file system. After doing this I tried installing again. The installation stopped at 95% and said that it couldnt install grub. 

So on the next attempt on the final installation page before installation I clicked on advanced and changed the grub installation from /dev/sda to /dev/sda1 (same location as my ubuntu install). The installation was successful and reached 100%. When I restarted however, after the normal aspire one startup screen, Ubuntu doesn't boot up. all that is displayed is a cursor. 

How do I get this OS to bootup?:confused:

---

### Post by oldfred on 2010-04-09
The BIOS transfers control to the MBR. The MBR is the first sector of the drive and is not part of the partition. You can install boot loader (windows does) into the partition (PBR) but have to have a chainloader either from the MBR or another boot somewhere.

If you installed to sda1, you installed to the PBR and do not have a boot loader in the MBR. Does you BIOS have some write protection on the boot sector to prevent overwriting the MBR? I am not sure what else might prevent writing the MBR.

You need to reinstall grub to the MBR.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by timoross on 2010-04-09
Here is a link that explains the problem even further. The offered solution in the link definitely doesnt work. [http://gparted-forum.surf4.info/viewtopic.php?id=13825](http://gparted-forum.surf4.info/viewtopic.php?id=13825) 

When I try mounting the device in the terminal it just says fs type wrong or bad super block, and I know I've formatted it as ext2. Gparted sees it as an unknown after formatting it. When I did dmesg |tail 
I got some errors including:
end_request: I/O error, dev sda, sector 63
ata2: EH complete
EXT2-fs:Couldn't read superblock on 2nd try.

This problem only occurred after I tried to install ubuntu on the drive, it kept getting stuck at the partitioning part. Now to make matters worse I can't eve install the linpus distro that came with the machine, because ubuntu has messed up the ssd.

Does ubuntu have the correct drivers for ssd drives? Can I install some somehow?

---

