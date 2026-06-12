---
title: "Windows Boot Loader"
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by Zuul47 on 2010-11-29
I was wondering if i could reinstall the windows bootloader with the ubuntu installation cd....because with the current ubuntu installation the windows 7 installation dvd doesnt load up. when i use a windows xp cd, the computer tells me that there is no active hard drive. other linux distros work just fine

any thoughts please post

---

### Post by oldfred on 2010-11-29
You cannot use XP to fix Vista or 7 and vice-versa. The partition boot sector and boot files are different.

If grub will not boot windows, it probably is a windows issue that needs repair.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

oldfred's Windows Vista/Win7 repair links:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)

---

### Post by Zuul47 on 2010-11-30
> **oldfred said:**
> You cannot use XP to fix Vista or 7 and vice-versa. The partition boot sector and boot files are different.

If grub will not boot windows, it probably is a windows issue that needs repair.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

oldfred's Windows Vista/Win7 repair links:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)

will the command install the mbr alongside grub?
thanks for the help!!!!

---

### Post by wilee-nilee on 2010-11-30
> **Zuul47 said:**
> will the command install the mbr alongside grub?
thanks for the help!!!!

No it will replace it, what actually is installed on the computer and what is your final goal here?

---

### Post by oldfred on 2010-11-30
If you do not want to just boot windows, then we need to see what is missing. Link also in wilee-nilee's signature.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] here [ /code] tags.

---

### Post by Zuul47 on 2010-11-30
> **wilee-nilee said:**
> No it will replace it, what actually is installed on the computer and what is your final goal here?

I want to remove Ubuntu from the computer, and reinstall Windows 7.
Ubuntu is installed on the whole hard drive. i know when i installed ubuntu there was an a custom bootloader option during the installation process, but i don't know if it will show the windows loader again.

---

### Post by wilee-nilee on 2010-11-30
> **Zuul47 said:**
> I want to remove Ubuntu from the computer, and reinstall Windows 7.
Ubuntu is installed on the whole hard drive. i know when i installed ubuntu there was an a custom bootloader option during the installation process, but i don't know if it will show the windows loader again.

Any legit windows DVD or loaded thumb should boot and install right over the Ubuntu. You can use a live Ubuntu cd and then gparted to just wipe Ubuntu first and even put a NTFS partition there. Turn off the swap when wiping though by right clicking on the swap partition in the Ubuntu install if there is one. I would make sure you can boot with the key prompt first before wiping and rebuilding the partitions.

Your computer has a per-session key prompt what is your computer model. Sometimes the cd/dvd reader being first in the bios doesn't work. The prompt on my computer is f12 immediately held down on powering up yours may be different might even be the esc key.

---

### Post by Zuul47 on 2010-11-30
thanks for the help  guys

---

