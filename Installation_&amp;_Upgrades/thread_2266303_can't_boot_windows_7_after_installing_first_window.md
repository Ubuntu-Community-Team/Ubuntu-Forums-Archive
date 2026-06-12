---
title: "can't boot windows 7 after installing first windows 7 and than ubuntu 14.04 LTS"
date: 2015-02-21
forum: Installation &amp; Upgrades
---

### Post by philip27 on 2015-02-21
Hello brave folk!
Oh well, after days of trying, I surrender and beg for advice, please:
here is the paste from boot-repair:
[http://paste.ubuntu.com/10346580/](http://paste.ubuntu.com/10346580/)

---

### Post by grahammechanical on 2015-02-21
Try loading into Ubuntu and running

```
sudo update-grub
```

and watch the printout to see if it detects a Windows boot loader. Right now the Grub configuration file that is used for the entries to the Grub boot menu has this title

> menuentry [COLOR=#BB4444]'FreeDOS (on /dev/sdb1)'[/COLOR] --class windows --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'osprober-chain-1E5D-925A'[/COLOR] [COLOR=#666666]{[/COLOR]
	insmod part_msdos
	insmod fat
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd1,msdos1'[/COLOR]
	[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**	  **[/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd1,msdos1 --hint-efi[COLOR=#666666]=[/COLOR]hd1,msdos1 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci1,msdos1  1E5D-925A
	[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**	  **[/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 1E5D-925A
	[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**	**[/COLOR]parttool [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#AA22FF]**}**[/COLOR] hidden-
	drivemap -s [COLOR=#666666]([/COLOR]hd0[COLOR=#666666])[/COLOR] [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#AA22FF]**}**[/COLOR]
	chainloader +1
[COLOR=#666666]}[/COLOR]

Why that says Freedos and not Windows boot loader I do not know but what happens when you select the option to load Freedos? Does that in turn load Windows. This is also confusing things in my opinion

> [COLOR=#666666]===================[/COLOR] os-prober:
/dev/sda6:Das aktuell benutzte Betriebssystem - Ubuntu 14.04.2 LTS CurrentSession:linux
/dev/sda1:Windows 7 [COLOR=#666666]([/COLOR]loader[COLOR=#666666])[/COLOR]:Windows:chain
/dev/sda2:Windows 7 [COLOR=#666666]([/COLOR]loader[COLOR=#666666])[/COLOR]:Windows1:chain

It seems that you have a Windows boot loader in the first partition (sda1) which Grub is referencing. And another Windows boot loader in the second partition (sda2) which should be chained to the first Windows boot loader if you are to load Windows from the Ubuntu (Grub) boot menu. Perhaps that is where the chain is broken - between the boot loader in sda1 and the boot loader in sda2.

Regards.

---

### Post by philip27 on 2015-02-21
Hi :-)
this is the reply: 
sudo update-grub
[sudo] password for philip: 
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-30-generic
Found initrd image: /boot/initrd.img-3.16.0-30-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done

---

### Post by philip27 on 2015-02-22
Hi, Thanks again!

It looks like the "sudo update-grub" already did it, I can now load into windows as well!

---

