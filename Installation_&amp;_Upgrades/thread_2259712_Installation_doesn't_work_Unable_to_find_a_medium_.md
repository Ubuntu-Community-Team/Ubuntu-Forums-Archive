---
title: "Installation doesn't work: Unable to find a medium containing a live file system"
date: 2015-01-06
forum: Installation &amp; Upgrades
---

### Post by wamgx on 2015-01-06
After burning a Lubuntu 14.04.1 LTS CD-RW with the standard Windows 7 burning tool, I get this result:

> BusyBox V.1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system

The CD boots normally, I select my language, but if I want to install it or if I select the "Try Lubuntu without installing" menu, the same message appears.

Important detail: I'm trying to reinstall my Lubuntu installation because my precedent install (Lubuntu 14.10) refuses to boot up anymore. I gets stuck after a 'Verifying DMI Pool Data" message when turning my PC on.

Can anyone help me?

Thanks in advance :)

[COLOR=#141823][FONT=Helvetica]EDIT: I've tried making an USB with the Universal-USB-Installer-1.9.5.8 tool on Windows 7 but it just refuses to boot from the USB.[/FONT][/COLOR]
[COLOR=#141823][FONT=Helvetica]I've set USB-FDD, USB-ZIP and USB-CDROM as the first, second and third boot device respectively but it doesn't work. I've got a "'Verifying DMI Pool Data" message in the GRUB and then nothing happens.[/FONT][/COLOR]

[COLOR=#141823][FONT=Helvetica]My boot options in the BIOS are:[/FONT][/COLOR]
[COLOR=#141823][FONT=Helvetica]Floppy[/FONT][/COLOR]
[COLOR=#141823][FONT=Helvetica]LS120[/FONT][/COLOR]
[COLOR=#141823][FONT=Helvetica]Hard Disk[/FONT][/COLOR]
[COLOR=#141823][FONT=Helvetica]ZIP100[/FONT][/COLOR]
[COLOR=#141823][FONT=Helvetica]USB-FDD[/FONT][/COLOR]
[COLOR=#141823][FONT=Helvetica]USB-ZIP[/FONT][/COLOR]
[COLOR=#141823][FONT=Helvetica]USB-CDROM[/FONT][/COLOR]
[COLOR=#141823][FONT=Helvetica]LAN[/FONT][/COLOR]
[COLOR=#141823][FONT=Helvetica]Disabled[/FONT][/COLOR]

---

### Post by wyliecoyoteuk on 2015-01-06
Verifying DMI pool data is a bios message.
If it doesn't get past that, it may mean that there is a hardware fault.

---

### Post by wamgx on 2015-01-06
I was afraid it might be hardware related but apparantly ... it is not.

I ended up installing Linux Mit 17.1 Cinnamon from a DVD, it went just fine. That's not an ideal situation cause Linux Mint is a lot more resource-hungry than Lubuntu on my 8 year old machine... but at least, I've a usable PC now. I suppose there's a bug in the Lubuntu installer (I'm 100% sure my Lubuntu installation disc was fine), I'll give Lubuntu 15.04 a try when it comes out.

Thanks for the help wyliecoyoteuk ;)

---

### Post by wyliecoyoteuk on 2015-01-06
It may just be that the lubuntu patition table was corrupt.

---

