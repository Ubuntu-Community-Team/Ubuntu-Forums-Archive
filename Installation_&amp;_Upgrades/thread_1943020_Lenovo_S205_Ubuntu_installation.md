---
title: "Lenovo S205 Ubuntu installation"
date: 2012-03-18
forum: Installation &amp; Upgrades
---

### Post by frncz on 2012-03-18
I recently bought a Lenovo S205. After many days of experimentation, I am running out of ideas about how to install Ubuntu on this laptop.

I long ago 'destroed' the Windows 7 installation and have reformatted the hard disk in many ways, but I am still defeated. I followed instructions on
[http://helms-deep.cable.nu/~rwh/blog/?p=177](http://helms-deep.cable.nu/~rwh/blog/?p=177)
and on many other pages, but to no avail. 
The installation process works fine, with oneiric and precise using AMD64, and also with the alternate downloads, but the S205 just does not boot into Ubuntu. The USB prepared with the startup disk creator works fine, but I have not had any success with unetbootin.
I lat theinstallation program take care of the partitioning, and I also manually partitioned to have a 200Mb fat32 uefi partition with separate / and /home ext4 partitions. I tried a dos partition and a /boot partition, to no avail. The machine never boots anymore, unless I have a USB slotted in. This is fine for a while, but snce I probably will need to reformat the hdd, it is quite useless.

I would love some help. I am well used to installing Ubuntu on many machines - but now I am defeated.

Cheers

---

### Post by yavez on 2012-03-25
> **frncz said:**
> I recently bought a Lenovo S205. After many days of experimentation, I am running out of ideas about how to install Ubuntu on this laptop.

I long ago 'destroed' the Windows 7 installation and have reformatted the hard disk in many ways, but I am still defeated. I followed instructions on
[http://helms-deep.cable.nu/~rwh/blog/?p=177](http://helms-deep.cable.nu/~rwh/blog/?p=177)
and on many other pages, but to no avail. 
The installation process works fine, with oneiric and precise using AMD64, and also with the alternate downloads, but the S205 just does not boot into Ubuntu. The USB prepared with the startup disk creator works fine, but I have not had any success with unetbootin.
I lat theinstallation program take care of the partitioning, and I also manually partitioned to have a 200Mb fat32 uefi partition with separate / and /home ext4 partitions. I tried a dos partition and a /boot partition, to no avail. The machine never boots anymore, unless I have a USB slotted in. This is fine for a while, but snce I probably will need to reformat the hdd, it is quite useless.

I would love some help. I am well used to installing Ubuntu on many machines - but now I am defeated.

Cheers

I'm in the same boat.  Tried everything, including this guide (in German, needs a google translate) [http://forum.ubuntuusers.de/topic/tutorial-ubuntu-11-04-auf-lenovo-s205-installi/](http://forum.ubuntuusers.de/topic/tutorial-ubuntu-11-04-auf-lenovo-s205-installi/)  but still no joy.  Tried all the 'buntus, all the mints, Fedora (including 17 Alpha), Suse, Fuduntu and if I wasn't completely fed up, I'd probably try to install Amiga OS on this machine because I would probably have just as much luck. :(

Apparently it's Grub2 that's at fault, from what I've read, but  that doesn't help much in getting my machine up and running.  And this time nobody can blame hardware vendors for not relasing so-and-so drivers, because the original Grub apparently works fine (although I can't get the sodding thing to work at all).  So, after a good few years Windows free and Linux happy, I've finally had enough.  Unity, Gnome 3 and KDE4 DE abominations, ridiculous and convoluted wireless set-ups (you have to blacklist and remove an Acer driver to make the wireless work in the s205), broken graphics drivers, a plethora of changes made for changes sake, now you've got to edit config files and downgrade packages just to boot the damn machine.  Everything feels less cohesive than when I first used Warty.

Good luck to you.  Hope you can get your problems sorted out. I'm going back to the Borg. ;)

---

### Post by oldfred on 2012-03-26
I just copied this for another user.

There is a thread on s205 issues with efi.

Examples that worked, format in advanced with gparted, gpt with find efi output & demesg
[http://ubuntuforums.org/showthread.php?t=1939094](http://ubuntuforums.org/showthread.php?t=1939094)
How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)

Are you booting with MBR & BIOS or UEFI and gpt?  Or gpt & BIOS. I do not have  a Lenovo but use gpt with BIOS and have to have a bios_grub partition. If booting with UEFI, you use gpt and the first partition must be efi.

---

### Post by yavez on 2012-03-28
> **oldfred said:**
> I just copied this for another user.

There is a thread on s205 issues with efi.

Examples that worked, format in advanced with gparted, gpt with find efi output & demesg
[http://ubuntuforums.org/showthread.php?t=1939094](http://ubuntuforums.org/showthread.php?t=1939094)
How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)

Are you booting with MBR & BIOS or UEFI and gpt?  Or gpt & BIOS. I do not have  a Lenovo but use gpt with BIOS and have to have a bios_grub partition. If booting with UEFI, you use gpt and the first partition must be efi.

Neither of those links did anything for me, but my few days with the Borg convinced me to keep searching for an answer.  Which I found, and I'm now running Linux on the s205 (Linux Mint 12 LXDE) thanks to this review/guide: [http://community.linuxmint.com/hardware/view/8871](http://community.linuxmint.com/hardware/view/8871) :guitar:

---

