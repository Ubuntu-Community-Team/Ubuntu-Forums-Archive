---
title: "Dual boot Unbuntu and Windows Vista from an Everex Impact GC3502 (How to)"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by transporter_ii on 2007-12-24
This is just some notes I made on doing a dual boot system with Ubuntu and Windows Vista and I thought it might help someone out, as I noticed a lot of people with issues with SATA and IDE drives in the same system. -- Transporter_ii

 -=-=-=-=-=-=-

Dual boot Unbuntu and Windows Vista from an Everex Impact GC3502

The computer comes with Vista preinstalled on an 80 Gig SATA drive. I put 2 160 Gig IDE drives in the computer and installed Ubuntu 6.06 LTS from a Live CD onto the Master IDE drive. Note that only the IDE drives show up during the Ubuntu install. At this point, the SATA drive was the one that booted up at a reboot. Since I read conflicting information on Windows Vista and Grub, I tried OSL2000 and GAG (neither worked, but I liked GAG better) and installed OSL2000 onto the SATA drive (later, I tried installing GAG onto the IDE Master drive). With OSL2000, it would find the Linux drives, but GRUB would throw up an "error 17" and say there was no bootable file system on it while trying to boot. The Windows Vista drive, booted fine, however. 

Here is what I ended up doing:

In the system BIOS, I moved the master IDE drive's Hard Disk Boot Priority (Note that this is not the same as the "First Boot Device") up to number 1.

This reversed my situation and made the Ubuntu drive boot, but the Windows drive now would not. This is the point where I installed GAG onto the master IDE drive, which is now the drive that boots. Unforuately, it was still a no go. GAG would not boot the Windows SATA drive. So at this point, I reinstalled grub using a super-grub cd-r I downloaded (which appears to be a good, easy way to uninstall GAG, by the way).

Finally, I found out how to find the Windows Vista SATA drive and just added it to Grub.

What you have to do is hit "Esc" in the Grub menu and drop to the command line. From there do the following:

  grub> root (hd    [And press the TAB key]

This will display something like this:

Possible disks are: hd0 hd1 hd2 hd3

And next type this:

  grub> root (hd0,  [And press the TAB key]

This will display the partition information on the drives. So what you want to do is do this for each drive in your system, which you should have found above.

In this instance, I had:

  hd0 ext2fs file system
  hd1 unknown file system
  hd2 ext2fs file system
  hd3 unknown file system

There may be a more scientific way to do this, but since I knew the Windows Vista drive couldn't be hd0 or hd2, I booted into Unbuntu and opened a terminal window, where I issued a "sudo su" command, and changed directory to "/boot/grub". There you can edit the menu.lst item with the following:

title                  Windows Vista
rootnoverify     (hd3,1)
map                 (hd3) (hd0)
map                 (hd0) (hd3)
chainloader +1
makeactive
boot

Now like I said, I wasn't scientific about it, I did trial and error using hd1 and hd3 until I hit the Windows Vista partition and it booted right up. Using hd1 in the above example, I booted the Windows Vista Recovery partition (Which attempted to boot but exited out with an error a minute or so into the boot). And if I understand Grub syntax correctly, in the "(hd3,1)" shown above, the 1 is a partition on the hd3 drive. I actually trial and errored this, too, and the 0 partition would not boot, but the 1 booted right up and I had my first dual boot system.

The above is a working Grub menu.lst item that works for me. The only thing I can suggest is making a backup of the above, because after I got everything going, I updated Ubuntu, and I'm not sure where or why, but the Grub menu.lst file was replaced with a default one, and I had to do this all over again. To backup the menu.lst file, I just issued the command, "cp menu.lst menu.vista.working.lst" and hit enter. That way if it ever just disappers again, at least I have a copy of it.


Transporter_ii

---

### Post by transporter_ii on 2007-12-29
A note on an Everex GC3502. 

The VIA chipset is:

Northbridge: VIA CN896
Southbridge: VIA VT8237A 


Support for this chipset is NOT in 6.06 LTS. 6.06 will work fine as long as you install to an IDE drive, but the SATA drive will not show up. If you want to access the SATA drive, you will have to go to 7.10 (or at least I know 7.10 solved my problem of the SATA drive not showing up).

Transporter_ii

---

