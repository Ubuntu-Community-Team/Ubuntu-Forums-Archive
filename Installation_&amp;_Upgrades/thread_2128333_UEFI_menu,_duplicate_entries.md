---
title: "UEFI menu, duplicate entries"
date: 2013-03-22
forum: Installation &amp; Upgrades
---

### Post by Stephen_at on 2013-03-22
I've installed 12.0.4 alongside windows 8 on a UEFI based system.

It boots into Linux fine from its menu and it boots into Windows 8 if I pick the third option on the menu - which doesn't have a sensible name

I also have lots of menu entries that seem to be duplicates.

So how can I get rid of those duplicate entries and change the oddly titled menu entry to boot Win 8

Here's my boot info

[http://paste.ubuntu.com/5638437/](http://paste.ubuntu.com/5638437/)

---

### Post by Stephen_at on 2013-03-23
I should possibly point out that in the UEFU boot settings in the BIOS menu I see two linux boot options and two Windows boot options which ties in with the fact that the info from boot repair sees two partitons ( sda2 and sda3) with boot entries on them

The Boot menu has these options:

[FONT=Courier New]Ubuntu
Advanced Options for Ubuntu
Windows UEFI recovery bootmgfw.efi
Windows Boot UEFI Recovery
Windows UEFI recovery bootmgfw.efi sda3
Windows UEFI recovery sda3
Windows EUFI recovery LrsBootmgr.efi
Windows Boot UEFI recoverry bootx64.efi
Windows Boot UEFI recoverry bootx64.efi sda7
Windows Recovery Environment (loader) (on /dev/sda3)
Windows 8 (loader) (on /dev/sda5)
System setup
[/FONT]

If I can't get rid of the extras I'd like to rename "Windows UEFI recovery bootmgfw.efi" (item 3) to Windows 8

---

### Post by oldfred on 2013-03-23
All the entries in 25_custom were created by Boot-Repair by finding efi files on your system. The files that say on sda3 or on sda5 are from grub2's os-prober which has a bug and creates BIOS type entries that will not work with UEFI.
 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'


You can turn off os-prober (maybe when bug is fixed you can turn it back on?) to eliminate the last two entries.
       gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executable bit
sudo chmod a-x /etc/grub.d/30_os-prober
# Then do:
sudo update-grub

Because all the entries in 25_custom were created by Boot-Repair you can edit at will. I might back it up in case you need an entry to get into recovery later, but you can delete all but the one Windows entry that works and rename it anything you like.
      
 sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkup25_custom
gksudo gedit /etc/grub.d/25_custom
Then do:
sudo update-grub

Your sda2 partition ([COLOR=#ff0000]        D473-6C3C)[/COLOR] is the efi partition and sda3 has recovery boot files in it. So you may not need recovery files normally and can delete all boot stanzas refering to that UUID.
      
 /dev/sda2       2,050,048     2,582,527       532,480 EFI System partition
/dev/sda3       2,582,528     4,630,527     2,048,000 -

   /dev/sda2[COLOR=#ff0000]        D473-6C3C[/COLOR]                              vfat       SYSTEM_DRV
/dev/sda3        E873-C276                              vfat       LRS_ESP

---

### Post by Stephen_at on 2013-03-23
Its all moot - it crashed in Win8 and went into recovery which failed and got stuck in a loop and wouldn't boot into any sort of recovery mode. So I no longer have the laptop

Frankly this whole UEFI mess needs to be sorted out - right now its looking like Microsoft are winning. Having to install ubuntu and then install boot-repair manually is frankly a bit of a fiasco, and with a "Critical" bug in Grub which is still unassigned after 8 months which involves you having to edit files to fix messes it looks like its not going to get any better any time soon. 

We need to have it so it just works... but unfortunately the "just hack things about and edit things" reputation of Linux seems to be very much to the fore here.

---

