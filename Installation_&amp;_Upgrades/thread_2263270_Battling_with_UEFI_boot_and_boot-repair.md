---
title: "Battling with UEFI boot and boot-repair"
date: 2015-01-30
forum: Installation &amp; Upgrades
---

### Post by lawrence10 on 2015-01-30
Hi,

I installed Ubuntu 14.10 but it wouldn't boot, it took several hours to get a working system. I've managed, but I'd just like to document this because I couldn't find any relevant writeups online and the problem seems so simple that I'm surprised it just didn't work out of the box.

I received a new Acer Aspire E1-572G, I took out the pre-installed Windows disk (after just checking that it booted OK) and replaced it with a blank SSD. I dd'd the 64-bit 14.10 to a USB key and I had some problems booting from it, but it finally worked (apparently you have to enable UEFI, disable secure boot, and then disable UEFI, whereupon the secure boot checkbox disappears . . .) FWIW I tried the dd because it works on non UEFI machines, and all the Ubuntu tutorials on how to create a bootable USB key assume you're starting from Windows or from Ubuntu with cool special programs, never from another Linux or some other Unix.

After booting I installed Ubuntu, entire disk encrypted LVM (it's a laptop after all), rebooted... and nothing: "No bootable device -- insert boot disk and press any key". It bears mentioning that the "press any key" is a lie, it'll retry PXE but it won't boot USB unless it's from a cold boot. I tried with UEFI, and I get a different error message (text graphics reminiscent of linux kernel make menuconfig) but same meaning, nothing bootable found.

I booted the live USB to check that the disk looked OK (a half gig "Microsoft basic" partition, then a small 244MB linux partition, then the rest as a Linux partition. I followed the boot-repair doc on <https://help.ubuntu.com/community/Boot-Repair>, and I used default repair, no good. <http://paste.ubuntu.com/9959580>

Since it didn't work I looked at the paste and saw that it was putting the bootable flag on the big third partition. Not likely to work, since that can only be the encrypted LVM FS. I tried to put it on the /boot FS (the 244MB one), <http://paste.ubuntu.com/9961213>, but no luck either, so I tried the Microsoft one, and yay it works. I didn't see a grub menu, but I imagine it'll be there if I hold shift.

When I use fdisk to look at the disk it says that all partitions are EFI, when I use parted it says that they are all "boot, esp". I suppose that this is boot-repair at work, and that I should set the second partition to Linux 83 and the third to whatever encrypted LVM should be (83 also IIRC).

So . . . why didn't things work perfectly the first time? The Ubuntu install knew to make a vfat file system with grub files, it should make it bootable too, and boot-repair is smart enough to identify the EFI directory on the VFAT partition that is first on the disk, why isn't the default to make that bootable? Why, the second time I ran it it wanted to put the bootable flag on the USB key!

Now on to getting a sensible window manager that will not only let me copy text from or to a window without bringing that window to the front (pet peeve), but will also let me open several different terminals at once (the default terminal does, but not the xterm or UXterm left-hand launch squares -- I still have difficulty believing my eyes).

---

### Post by oldfred on 2015-01-30
With UEFI and gpt partitioning, the boot flag should only be on the efi (ESP) partition which must be FAT32 formatted.

And there was another thread where a flash drive had the strange two partition layout. I think there may be a bug on that issue. But it would be correct to have boot flag on the partition with the efi boot files.

The grub.cfg in the efi partition is just 3 lines and configfile to load the real grub.cfg in your /boot.


 Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
      
 Acer E3 requires UEFI password to allow added settings Post #8
[http://ubuntuforums.org/showthread.php?t=2253311](http://ubuntuforums.org/showthread.php?t=2253311)
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)
Acer E1-531 UEFI menus.
[http://www.tomshardware.com/forum/65627-63-body](http://www.tomshardware.com/forum/65627-63-body)
Herman's 2014_02_09 - My Adventure with Secure Boot in an Acer Aspire E1-531 Laptop
[http://members.iinet.net/~herman546/2014_02_09%20-%20My%20Adventure%20with%20Secure%20Boot%20in%20an%20Acer%20Aspire%20E1-531%20Laptop.html](http://members.iinet.net/~herman546/2014_02_09%20-%20My%20Adventure%20with%20Secure%20Boot%20in%20an%20Acer%20Aspire%20E1-531%20Laptop.html)

---

### Post by lawrence10 on 2015-01-31
I created a bug for the installer on launchpad. boot-repair wasn't on the install ISO, so I won't bother. Marking thread as solved

---

