---
title: "Lockup installing on Compaq Proliant 2500"
date: 2006-06-21
forum: Installation &amp; Upgrades
---

### Post by rwright142 on 2006-06-21
install locks up with error:
"AT Translated Set 2 keyboard on ISA0060/Serio0"

At the boot prompt I have tried:
"bootkbd=es"
"pci=noacpi" (got "Could not find kernal image: pci=noacpi" error message)
"server"
"server server-expert"
[ENTER] for default
"noapic nolapic"

The server has been retired for quite some time and the company I just started working for was going to throw it out. I thought I could use it for experimenting with ubuntu. It is a Pentium II, 200MHz with 512MB RAM. I have 1 18GB SCSI drive.

Any ideas?

Thanks in advance...

---

### Post by CasualMan on 2006-06-26
[QUOTE=rwright142]install locks up with error:
"AT Translated Set 2 keyboard on ISA0060/Serio0"

At the boot prompt I have tried:
"bootkbd=es"
"pci=noacpi" (got "Could not find kernal image: pci=noacpi" error message)
"server"
"server server-expert"
[ENTER] for default
"noapic nolapic"

The server has been retired for quite some time and the company I just started working for was going to throw it out. I thought I could use it for experimenting with ubuntu. It is a Pentium II, 200MHz with 512MB RAM. I have 1 18GB SCSI drive.

Any ideas?

Thanks in advance...[/QUOTE]

I have a Compaq Proliant 800 Model 6/200 (dual-cpu Pentium Pro's @ 200Mhz) with 128Mb RAM & 4Gb IDE hard drive. It won't run Ubuntu 6.06 (Dapper Drake). I've had to reinstall 5.10 (Breezy Badger). However when I installed all of the updates, I lost the ability to go on the Internet (I think my Ethernet card is not being recognized). I recommend you download the older versions of Ubuntu to try (5.04 Hoary Hedgehog and 5.10 Breezy Badger). Be careful installing upgrades though. You may want to install them one at a time so that if one mucks up the works you can hopefully fix it.

*UPDATE*
After reinstalling 5.10 and confirming that I could go online, I followed to the letter the very excellent upgrade instructions at "http://www.ubuntuforums.org/forumdisplay.php?f=140" on how to upgrade from 5.10 to 6.06. This time I did not install any upgrades to the 5.10 OS but immediately began following the advice on how to upgrade to 6.06. It took about 24 hours to complete the reinstall and upgrade, but 6.06 is up and running now; I'm using it here to edit my reply.

Thank you UBUNTU community!! I'm one small step closer to a windows-free computing environment (server & desktop done, now to work on my notebook!)

---

### Post by igknighted on 2008-04-08
So... I'm bumping this ANCIENT thread because I just acquired one of these from work (it had been collecting dust and was going to be disposed of...).  I can boot into windows 2000 which is on it now, but have been unable to get any Solaris, BSD or Linux CDs to boot.  Oh...  and the only way Win2k boots is by selecting the first HD as the boot device from a linux CD's boot menu.

I get an error during the boot sequence (what I would assume would be during BIOS) that the BIOS is not installed, but I don't know if this is the RAID card's bios or something else.

Any ideas on how to get this machine up and running on something other than windows (because for the love of god, who wants to run a GUI on a pentium pro 200mhz?)?

---

