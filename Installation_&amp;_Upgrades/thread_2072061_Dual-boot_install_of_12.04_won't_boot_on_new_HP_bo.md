---
title: "Dual-boot install of 12.04 won't boot on new HP box"
date: 2012-10-17
forum: Installation &amp; Upgrades
---

### Post by coastwatcher on 2012-10-17
1.  We received an HP p7-1232 for my wife today (8GB RAM, 1TB disk), and I set out to install Xubuntu 12.04-amd64 on half the disk.  The machine comes with the Windows installation on 3 partitions (SYSTEM, C, and HP_RECOVERY), so I had the install shrink the C drive by half and use that space for Linux.  The install gave me /dev/sda5 (/) and /dev/sda6 (swap).  I had my doubts about booting Linux without a primary /boot partition, but I assumed that the installer knew what it was doing.  The installation process reported no errors, but when I tried to reboot the HDD in Ubuntu, I wound up back in Windows.

2.  I then booted the install media again and did manual partitioning to get the Linux root on a primary partition.  I deleted /dev/sda[56], created /dev/sda4 as a primary partition in place of the extended partition, and installed on that.  (The install warned about the lack of a swap partition, but I figured I could create a swap file after the initial boot.)  Again, the install process reported no errors, but booting the HDD put me back in Windows.

3.  Boot the install media, choose repair, and install grub a second time on /dev/sda4.  Reboot the HDD: Windows again.  By now this was becoming tiresome.  :-)

4.  Boot the install media, repair, shell with /dev/sda4 as the root.  I then used fdisk to remove the bootable flag from /dev/sda1 (Windows System) and add it to /dev/sda4 (Linux).
This time booting the HDD said "Missing operating system".

5.  I suspect that I need some command-line magic to install grub properly from the repair shell, so the machine can boot into Linux, but I am finding the grub documentation a trifle opaque.  Should I install grub on /dev/sda, in the 2048 sectors before the first partition?  Will it even fit there?  Do I need to do something more to ensure that grub will give us a choice between Ubuntu and Windows?

I'm a long time happy Xubuntu user, but I scrubbed all the MS bits off the disk the first time I powered my system up: no dual-boot for me.  That's not (yet) an option for my wife, though we might get there eventually.

Does anyone have any suggestions?  Thank you.

--CoastWatcher

---

### Post by coastwatcher on 2012-10-19
The solution was to run Boot-Repair from the Ubuntu-Secure-Remix disk.  I found that in a reply to another thread in the forum.

This machine can apparently boot optical and USB devices in either legacy (bios) or EFI mode, but the HD only boots in legacy mode, and the initial install had guessed wrong, installing boot.efi instead of boot.pc

Now, how do I mark the thread as [SOLVED]?

---

### Post by BlinkinCat on 2012-10-19
> **coastwatcher said:**
> The solution was to run Boot-Repair from the Ubuntu-Secure-Remix disk.  I found that in a reply to another thread in the forum.

This machine can apparently boot optical and USB devices in either legacy (bios) or EFI mode, but the HD only boots in legacy mode, and the initial install had guessed wrong, installing boot.efi instead of boot.pc

Now, how do I mark the thread as [SOLVED]?

You can mark thread as "solved" using thread tools at top of page - :)

---

