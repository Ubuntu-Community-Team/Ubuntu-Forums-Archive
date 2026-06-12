---
title: "Ubuntu, Windows Vista, Windows XP downgrade issue"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by goffy59 on 2008-03-04
Basically awhile ago I thought it would be nice to have all 3 on my computer. Lately I haven't been using Vista and now its a waste of space. I like Ubuntu and Windows XP fine. I want to get rid of Vista but then I run into Boot problems. As you all probably know; grub allows me to choose longhorn/etc to boot to Vista and then Vista lets me boot to Windows XP. How can I delete Vista and KEEP Ubuntu and Windows XP without losing any of my data or settings. I've thought about deleting Windows Vista and then running repair MBR on Windows XP recovery console, but then that would delete Grub! Anyhow, I was wondering if anyone had a working method that usually works great. I don't want to ponder into something and then have to reinstall all my stuff. Does anyone share the same caution I do? Windows is not very flexible and I don't want anything bad happening. Anyhow, thanks in advance.

---

### Post by mikewhatever on 2008-03-05
Are you sure you have to boot XP through Vista? Isn't there an entry in GRUB for XP? Can you post the output of cat /boot/grub/menu.lst.

---

### Post by goffy59 on 2008-03-16
Not so much of and issue anymore but I would like to know how to do this. Yes, you HAVE to boot to the LONGHORN/vista loader to boot to windows xp(because Windows uses an older loader, same as windows 2000). Its like a chain; Grub>Longhorn>NTLDR(Windows xp/2000). I don't know why microsoft had to change it, but they did(bastards). So if I get rid of Vista, it messes up xp. If I were to use fix mbr/fix boot command in recovery console it would seriously mess up grub. I just was wondering if there was a safe way to do this without ruining my installations. Basically... keep Ubuntu/Windows XP and get rid of Vista. Excuse my spelling grammar. :(

Thanks in advance!
-Goffy

---

### Post by goffy59 on 2008-03-18
Bump*

---

### Post by jimv on 2008-03-18
Go ahead and wipe out your Vista partition.  Then go into Ubuntu, and put your XP disk in.  Copy NTLDR and NTDETECT.COM from the i386 folder on the XP disk to the root of your XP partition.  Then, if there's not a BOOT.ini file on your XP partition, you'll need to make one.  Just create a new text file, call it BOOT.INI and paste this into it:

[INDENT][boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=&#8221;Microsoft Windows XP Professional&#8221; /fastdetect[/INDENT]

Replace the partition(1) with the number of whatever partition you have XP (1, 2, 3, etc)

Vista uses a different kind of boot loader than XP...different files and everything.

---

### Post by goffy59 on 2008-03-19
Thank you very much! It worked out wonderfully.

---

