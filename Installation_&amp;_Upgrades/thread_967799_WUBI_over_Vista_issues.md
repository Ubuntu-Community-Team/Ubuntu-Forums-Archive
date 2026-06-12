---
title: "WUBI over Vista issues"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by kordasn on 2008-11-02
Hi Everyone,

What I'm really trying to do is to tri-boot Vista, XP and Ubuntu (8.10/whatever is the one you could download yesterday at 3pm EST).  I have the Vista (Business/SP1) and XP(Pro/SP3) partitions up and running happily; they both run through the Vista bootloader (setup using EasyBCD).  They're on the first and second 50Gb partitions respectivly, running NTFS.  The rest of the drive is empty(ish).  I guess I should give some sysinfo?  It's a Dell Inspiron 6000 laptop, has 1.83 / 2GB / 160 GB.  

So I first tried to follow the steps from ([http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm))

Eventually that didn't work, I got GRUB error 18 on first startup.  I tried to play around with GAG and EasyBCD to get it to work, it didn't.  (I have no problem going back to try this again if someone knows what I did wrong or can guide me through a non-trivial install).  The only deviation from the plan that's mentioned there is that I didn't select the "Guided - use the largest continuous free space" option, because the bar looks like it takes 100% of HDD, and I do NOT want to re-install the other 2 OSs again.  I have tried 'manual' and 'guided -... resize.'  Both give me a GRUB error 18.

I've also tried following this:

[http://lifehacker.com/software/ubuntu/hack-attack-how-to-tripleboot-windows-xp-vista-and-ubuntu-193474.php](http://lifehacker.com/software/ubuntu/hack-attack-how-to-tripleboot-windows-xp-vista-and-ubuntu-193474.php)

Which is moderately similar to the previous one, it also left me with a GRUB 18.  Lastly I have tried WUBI,  with whatever version you can download as of 1h before this post.  I thought everything was going well, thought I wasted those 5 hours yesterday grinding my face into the other installs.  Well, it DLed, installed, restarted, even showed up in the Vista Bootloader(!), but then I get:


Status: 0xc0000001
Info: The selected entry could not be loaded because the application is missing or corrupt.

Unfortunately, that's where the story ends; despite there being a lot of information about Grub/18 (though none helped me in this case), there is not too much about WUBI and 0xc...1 error.  At the bottom of this email, I'm going to try to include some information about the boot records.

So really, what I want to end up with is make Ubuntu work with the setup that I have.  And at the moment, I'm not exactly sure where to proceed anymore.  I suppose what I really need is to waste someone's time helping me setup this.

In the event that someone supposes to re-install Ubuntu using guided/etc., (which is what I would tell someone if I just read all this text) could you please include what to do when you're stuck with a GRUB E.#18.  What I'm guessing (hoping) has to happen is to boot into Ubuntu live and use some partition voodoo magic to make it work.  I can also boot into the XP (and Vista, for the 2c that's worth) to have it work.

-Matt









Information:
-First the EasyBCD info (note I tried to make my own unix record and that also doesn't work properly)
-Second the menu.lst
-Third the (non-jibberish of) wubildr.mbr


EasyBCD:
There are a total of 4 entries listed in the Vista Bootloader.
Bootloader Timeout: 10 seconds.
Default OS: Microsoft Windows Vista

Entry #1

Name:  Microsoft Windows Vista
BCD ID:  {current}
Drive:  C:\
Bootloader Path:  \Windows\system32\winload.exe
Windows Directory:  \Windows

Entry #2

Name:  Microsoft Windows XP
BCD ID:  {89e901fd-a859-11dd-a44c-00123fe3d76b}
Drive:  C:\
Bootloader Path:  \NTLDR

Entry #3

Name:  Ubuntu
BCD ID:  {89e9020a-a859-11dd-a44c-00123fe3d76b}
Drive:  G:\
Bootloader Path:  \ubuntu\winboot\wubildr.mbr

Entry #4

Name:  NeoSmart Linux
BCD ID:  {89e9020b-a859-11dd-a44c-00123fe3d76b}
Drive:  C:\
Bootloader Path:  \NST\nst_grub.mbr






G:\ubuntu\winboot\menu.lst

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt






Not sure if it will help, but this is the end (the non jibberish) of the wubildr:

Press _ to start GRUB, any other key to boot previous MBR ..._
Timeout : _   ____
Invalid previous MBR. Press any key to start GRUB ..._
Cannot find GRLDR._ to hold the screen, any other key to boot previous MBR ..._
Error while reading MBR of _drive (hd0 ) _
Invalid boot indicator in partition table of _
Invalid sectors_per_track in partition table of _
Invalid start_sector in partition table of _
Invalid end_sector in partition table of _
No boot signature in partition table of _
Error: Cannot find GRLDR in all devices. Press Ctrl+Alt+Del to restart._
Try (hd0,0 ) : _EXT2: _NTFS4: _NTFS5: _NTFS5p: _FAT32: _FAT16: _FAT12: _non-MS: skip _Extended: _invalid or null _This partition is NTFS but with unknown boot record. Please
install Microsoft NTFS boot sectors to this partition correctly, or create an
FAT12/16/32 partition and place the same copy of GRLDR and MENU.LST there._____________________________hot-key_________GRUª

---

### Post by kordasn on 2008-11-02
Resolution:
Put WUBI on c:

---

