---
title: "GRUB install-Fatal error"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by ninadb on 2007-07-13
I have a new Core 2 duo system e6300 with 2 SATA HDD of 80gigs each and 1gig of RAM.
I have a intel DG965RY chipset. I downloaded the ubuntu feisty iso (desktop cd) and booted. I was surprised and amazed at the improvements over earlier versions Ubuntu had made.
I decided to install it on my 2nd HDD. Ubuntu shows this as sda and sdb .The install went very smoothly but after completing 94%
I got an error message "Cannot install GRUB to 'sdb' This is a fatal error." When I clicked ok the whole installation stopped.
Questions
1.I mounted the drive and saw that ubuntu has been installed... but do not know what the remaining 6% was as it aborts at 94%. is it possible to install GRUB now
2. I want to boot ubuntu from Windows bootloader and do not want to install GRUB on MBR
How do i do it from a live cd. Ubuntu shows the disks as sda and sdb.
I think I am giving some wrong numbers in the advanced section
what should be the correct drive numbers

Thanks
Ninad

---

### Post by ninadb on 2007-07-14
Hi

No replies to this topic almost frustrated me. So I decided to try installing changing the drive letters.

I entered (hd1) in the "Advanced" button for GRUB installation.

The installation went smoothly and completed successfully.

The next problem
As per the ubuntu guides and various other links I booted from the livecd and copied the mbr of my second hdd to a file. I copied the file to C:\ in windows and edited the boot.ini.
Now I have 2 entries XP and Ubuntu while booting.
When I select ubuntu only "GRUB" is shown on the screen and the computer hangs.

What could be the problem now.

I gave the following command
sudo dd if=/dev/sdb of=~/Desktop/linux.bin bs=512 count=1

Thanks
Ninad

---

