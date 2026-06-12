---
title: "mbr does not allow grub2"
date: 2011-09-29
forum: Installation &amp; Upgrades
---

### Post by Catsquotl on 2011-09-29
Hi,

After a few years away from Linux i thought to give it another go on my brand new laptop.
Windows 7 was pre-installes and there is a recovery partition present courtesy of Acer.

The initial install went well until it was time to reboot.
After reboot... Windows started without so much of a hint of ubuntu being installed.

I figured i did something wrong so I deleted the extended partition freed up some space and did the install again on 360 gb of unallocated space.. Again everything seemed to be working, but no bootloader.

I then used chrooted to the installed system and with the commands i found in this dutch wiki. 
[Herstel_Grub_2_met_een_LiveCD]("http://http://wiki.ubuntu-nl.org/community/Grub2/Grub2Herstel#Herstel_Grub_2_met_een_LiveCD")

Alas no avail.
So i downloaded the boot-repair-disk.
The rapair hinted at the fact that sda1 is nearly full and may be unable to boot.however windows is on hda3 and linux on hda5..

I am a bit reluctant to just wipe everything clean. Just got the laptop yesterday... Is there a way to install grub on a usb-stick and boot the installed ubuntu that is on my harddisk?

I don't understand fully why grub is unable to find its way to the mbr.
The boot-repair dump is here..
[http://paste.debian.net/132961]("http://paste.debian.net/132961")

ANy help will be higly appriciated..

Eelco

---

### Post by oldfred on 2011-09-29
Some BIOS has a setting that prevents writing into the MBR. Have you checked the BIOS?

Link to Dutch site did not work but I would not be able to read it. What error do you get or does it say it install grub2's boot loader to sda and then does not?

These were settings others have reported:
BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Disable Quickboot in BIOS 
core unlocker feature on asus m4a87td usb3 was causing the problem

---

### Post by Catsquotl on 2011-09-29
Its the latter problem..
It says it loads in sda but then doesn't...

I can't find any securityfeature in my Bios that may cause this.

[http://wiki.ubuntu-nl.org/community/Grub2/Grub2Herstel#Herstel_Grub_2_met_een_LiveCD]("http://wiki.ubuntu-nl.org/community/Grub2/Grub2Herstel#Herstel_Grub_2_met_een_LiveCD")
Here's the propper link (or so I hope)

ANyway I was thinking. On the live cd there used to be an option of booting an already installed system. There isn't one ond ubuntu 11.04.. But

Is there a way to do this? Maybe with an alternate install cd or something? I haven't fount one for 11.04 yet..

Eelco

---

### Post by oldfred on 2011-09-29
If you press a key as soon as the CD comes up (from the cd press any key at accessibility circle and keyboard), do you get a menu? But I think all that does it reboot to the hard drive.

Have you tried Supergrub?

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)
[http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk](http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk)

---

