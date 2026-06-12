---
title: "Windows not booting from GRUB2 after Ubuntu upgrade"
date: 2010-07-18
forum: Installation &amp; Upgrades
---

### Post by IAmNoodle on 2010-07-18
My girlfriend upgraded from Karmic 9.10 to Lucid 10.04 when the upgrade became available. She did it from Update Manager as opposed to a clean install. 

I have no idea what she did, or how the process works (I installed from a Live CD on my own computer) and ever since she did it, she hasn't been able to boot into Windows XP from GRUB2. 

GRUB2 loads up fine, with Ubuntu and Windows listed. It'll boot into Ubuntu with no problems. Selecting Windows will just re-load GRUB2. 

I've tried re-installing GRUB2 but that hasn't worked. My lack of imagination means I have no idea what to type in to Google, or the forum search. 

Is there any way to fix this?

---

### Post by oldfred on 2010-07-18
Many people upgrading mix up drives and partitions. You only install grub2 to drives.

When the instructions said all drives they meant sda, sdb etc not partitions sda1, sda2 sdb1 etc. You overwrote the windows boot sector in the windows partition.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If this is not the problem post back with this.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by IAmNoodle on 2010-07-31
That got things moving again! Thanks

One thing though. It now takes about a minute from switching the computer on to the system beep. It only took a few seconds before. Is there anything I can do to cut the new delay?

---

### Post by vitothegreat on 2010-07-31
Use EasyBCD.

---

### Post by oldfred on 2010-07-31
If it is system beep, not Ubuntu drums or windows, then it is something in BIOS. Are you running extended memory checks or mounting extra drives, trying to boot a non-bootable CD if CD set first in boot order. All those can take extra time before HD boots.

---

### Post by IAmNoodle on 2010-09-10
Just to let you know that the delay sorted itself out and everything is running fine again.

Thanks for your help guys

---

