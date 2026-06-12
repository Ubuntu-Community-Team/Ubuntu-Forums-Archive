---
title: "dual boot on two HD Windows /Ubuntu"
date: 2006-10-16
forum: Installation &amp; Upgrades
---

### Post by eeried on 2006-10-16
hello,

I'm about to install Ubuntu on the second slave HD of someone else's computer.  Windows is already installed on the master HD, taking up the whole HD (OS + documents).

I've read a few threads saying this set up was okay.

My question is about Grub: if you want to be able to choose between Windows and Ubuntu at boot time, do you install GRUB on hda?

I'm used to installing Ubuntu as dual-boot on the same HD (hda1) but this dual-boot on two HD will be a new experience -- I'd rather not loose Windows as this isn't my computer -- Windoze's long gone on mine but that was my choice!

Hope you can help me!

---

### Post by Kateikyoushi on 2006-10-16
The difference is that grub can be installed in two drives MBR.
I have exactly the same setup in one computer with two PATA drives and it installed flawlessly.

If you worry and the bios supports selecting boot device at startup, then you can remove the windows drive and install ubuntu when finished connect the windows drive mount it in ubuntu.
This way he can remove ubuntu anytime from the machine windows won't be effected.

You can also install with the alternate install cd that lets you select where to install grub, that way you don't have to disconnect the windows hdd at install.

---

### Post by gn2 on 2006-10-16
> **eeried said:**
> hello,

I'm about to install Ubuntu on the second slave HD of someone else's computer.  Windows is already installed on the master HD, taking up the whole HD (OS + documents).

I've read a few threads saying this set up was okay.

My question is about Grub: if you want to be able to choose between Windows and Ubuntu at boot time, do you install GRUB on hda?

I'm used to installing Ubuntu as dual-boot on the same HD (hda1) but this dual-boot on two HD will be a new experience -- I'd rather not loose Windows as this isn't my computer -- Windoze's long gone on mine but that was my choice!

Hope you can help me!

Hope this helps: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by Haegin on 2006-10-16
When i did an install on the same drive I just let ubuntu steal the mbr and it detected windows and added it to the boot list fine.

---

### Post by bulldog on 2006-10-16
Copied from another tread where I wrote it a half our ago.:D 

You must have the possebillity to set the bootdevice in your BIOS to do it my way.

I have a IDE master and a Sata which can be master as well slave.

I set the IDE as first bootdevice in BIOS and install windows on it.

Then select the Sata as bootdevice in BIOS and install Ubuntu on it.
[don't unplug your IDE hdd]

GRUB will be installed on the Sata drive and detects windows and add it to the menu.lst.
Also fstab will be up to date!

Only thing to do is to map your hdd's in menu.lst because windows likes to be on the first boot device.
Code:

# This entry automatically added by the Debian installer for a non-linux OS # on /dev/hda1 title Microsoft Windows XP Professional map (hd0,0) (hd1,0) map (hd1,0) (hd0,0) rootnoverify (hd1,0) savedefault makeactive chainloader +1

What I have achieved this way,I can boot windows and Ubuntu from GRUB,but if GRUB is corrupted for what reason,I can change the boot device in BIOS or by pressing F11 to change it to the IDE hdd and boot windows with its own bootloader.

This is the most comfortable way to use dual boot with two hdd's.

By the way,reinstalling GRUB with the live cd is very easy to do and cost no more as 10 minutes.

I'm much more concerned about gparted where you could erase the wrong partition and lose a lot of data by a mouse click.

---

### Post by eeried on 2006-10-17
Many thanks for all your replies and for the link! Sorry for not having found the right page on my own and thank you all for putting up with me. ;) 

bulldog wrote:
> I'm much more concerned about gparted where you could erase the wrong partition and lose a lot of data by a mouse click.
Oh I haven't dared to use Gparted nor the graphical installer. I love the Ubuntu-Debian-installer you have on the alternate CD. Partman (or whatever it is called on Dapper) is just great, flexible, clear and very safe, I find.

When installing Ubuntu on dual-boot with Windows I even use Knoppix and its Qtparted software to resize the Windows partition. It works like a charm on NTFS while it has never worked for me on Linux-type partitions. Then I make the Ubuntu or Xubuntu partitions (/ and /home) while installing from the alternate Dapper CD.

I'll read the thread carefully and see if I understand everything. I'll also have a good look at the computer and what Ubuntu Live-CD can tell me about it in a couple of days.

Cheers,

---

