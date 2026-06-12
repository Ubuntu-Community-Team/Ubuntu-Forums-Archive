---
title: "Clear/Reset MBR in Linux WITHOUT Windows being the Saviour??"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by OzzyFrank on 2007-01-15
Scenario: I seem to have multiple GRUB entries for the same drives (2 Ubuntu drives) after fixing corruptions of journal files by Demolinux "live cd" (not supposed to even touch my drives, but screwed both Linux drives nicely!!). Besides not wanting my bootloader (Acronis OS Selector) to keep automatically listing the multiples, I now can't get into my main Ubuntu drive after enlarging the partition, so wish to reinstall grub (to correct all of the above). Note that I HAVE already tried to reinstall grub, but it hangs before reaching grub when trying to boot it (the latest entry). The multiple entries (copies or whatever) in Acronis menu also go nowhere (after the menu), as when the grub menu is accessed it says the partition isn't there when i try to boot it. (No, all is fine, coz I could see files after mounting drive from other Ubuntu install, and I can force my main install to load by editing the other's grub options at boot. Also note the grub menus that complain the partition isn't there all point to the correct places, and obviously get the menu options from the drive, so go figure!).

So my drive and the install are fine, so am thinking too many links to grub in the mbr is what is keeping me from making a successful boot option in Acronis (for 2 installs, I have 10 different Linux options in Acronis that I can't delete as they keep coming back, so even if i could easily get into my main install, I would want to eventually clear this issue up!).

OK, so to clear the MBR (installing GRUB again will just make another that doesn't work) I have seen 2 suggestions, the main one being to use Windows, the other to use the DD command.

I want to avoid DD, as there is conflicting info on how many bytes to wipe etc, and big warnings on drives being made unbootable (and whole partitions being rendered unreadable!). Now, besides finding it amusing that so many people are ready to say "Oh, you have to use your Windows XP CD" to fix Linux (isn't it supposed to be the other way around?), I have to say I would rather find an easy (and safe) way to do this in Linux! Also, I am worried about "fdisk /mbr" (or "fixmbr" in XP) could do more than i want it to, since it is Fat32/NTFS based, and Linux is ext2/3. A lot of the time I see Linux people say to use fdisk or fixmbr it is to recover Windows drives (especially when totally uninstalling Linux) so want to make sure I can use this to safely clear an ext3 mbr (on a drive with no Windows) and then just run the Super Grub Disc to successfully reinstall the GRUB. I have seen a few that recommend fdisk/fixmbr for Linux drives/MBRs, but want to see what you guys reckon first!

PS: Is there any way to avoid these multiple/overlapping/conflicting MBR entries for GRUB? ie: When you setup GRUB in an MBR it wipes redundant entries for you? Or should I just install to partition (setup (hd2,1) instead of the usual setup (hd2)?).

Also, does the Linux "fdisk" have any use in this area? I gather not if Linux people are saying "Go grab a Windows disc"! (I have read a post where a pure Linux user had to contact Microsoft and pay for and order a boot CD just for clearing their mbr... that was almost too embarrassing to read!).

Thanks in advance!

---

### Post by deecee52 on 2008-03-21
Well this is over a year old  but I still have to respond. 

I must say as a new user of ubuntu the answer to grab windows disk is not the answer.

I don't have a win98 disk, and neither win2k or xp, let alone vista is not installed on the machine and I can't find a really good answer.

Help me banish windows from my vocabulary.

---

### Post by wernerz on 2008-03-21
Hi. I just found out how to do this with linux. It is the install-mbr command. It will install a new MBR but not the same one windoz fixmbr installs. In my opinion better!

Here is the command:

as root,

install-mbr -i n -p D -t 0 /dev/your-hard-drive (example hda)

The options used are

-i interrupt n = none (do not display a MBR prompt)
-p partition D =  boot the partition with the bootable flag set
-t timeout 0 = do not wait to boot

If you decide to install your bootloader (Grub or Lilo) to the MBR it will overwrite the MBR which is fine. Reset it with the install-mbr command.

The install-mbr man page is here: [http://xgen.iit.edu/cgi-bin/man/man2html?install-mbr+8](http://xgen.iit.edu/cgi-bin/man/man2html?install-mbr+8)  

I assume that your system has this command. If not just download it and install it. I install my boot loader to the root of the boot drive to leave the MBR untouched. However, not all distributions give you this option. 

Good luck and have fun with Linux! :)

---

