---
title: "Create a 2nd &quot;backup&quot; boot floppy and CLI question"
date: 2005-12-04
forum: Installation &amp; Upgrades
---

### Post by gene0915 on 2005-12-04
When I installed Ubuntu 5.10, I did not pick to install the bootloader onto my primary WinXP HD. Instead, I told the installer to create a boot floppy. When I want to boot Ubuntu, I make sure the 3.5" disk is in the floppy drive. In case this floppy ever gets corrupt, how can I make a backup of it? What Ubuntu command do I need to type to create another boot floppy?

I looked at the disk in Windows Explorer and it's empty. (But works perfectly)

Also... how do I make Ubuntu default to a cli interface at boot time. I want to issue: startx when I want the GUI loaded, otherwise I want it stuck at the cli.

Thanks!

---

### Post by bwog on 2005-12-05
To make boot floppies see: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253)
use /dev/fd0

Windows doesnt understand ext3 (I am happy with that), you can read files on ext3 partitions from windows with the program explore2fs.

---

### Post by gene0915 on 2005-12-05
[QUOTE=bwog]To make boot floppies see: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253)
use /dev/fd0

Windows doesnt understand ext3 (I am happy with that), you can read files on ext3 partitions from windows with the program explore2fs.[/QUOTE]

Call me dense but how will installing GRUB to /dev/fd0 help? Or will GRUB be smart enough to see the ext3 boot partition on HDC1 when the system is booting from floppy? I tried following that link and when I used /dev/fd0, I got some weird error about "BIOS"...."no drive".... (sorry, at work now and can't give the exact message) Instead of doing this via the CD and using "rescue", maybe I'll just try it after I normally boot into Ubuntu?

Or could I use Rawwrite in Windows and just read the floppy and write it to another one? Or maybe Winimage.exe in Windows or what's a Linux equivalent to Winimage?

---

### Post by bwog on 2005-12-05
The instructions I gave are a way to make a boot floppy. 

I have seen that error on my old machine, but I dont know how to solve it yet. (It is strange because your bios does recognize your floppies)

---

### Post by gene0915 on 2005-12-05
[QUOTE=bwog]The instructions I gave are a way to make a boot floppy. 

I have seen that error on my old machine, but I dont know how to solve it yet. (It is strange because your bios does recognize your floppies)[/QUOTE]

Yes, I have no problems with the floppy drive in Windows.

Also, know a way to start Ubuntu and have it dump me straight to the cli vs automatically loading X?

---

### Post by SilentCacophony on 2005-12-05
> Also, know a way to start Ubuntu and have it dump me straight to the cli vs automatically loading X?

This should do it, though there are many ways to do that. In a terminal:

**ls /etc/rc2.d | grep gdm**

and verify that you get **S13gdm** as the output, just in case... (some seem to have S99gdm, perhaps in older versions; if so replace the 13's with 99's in the following commands.) Then:

**sudo mv /etc/rc2.d/S13gdm /etc/rc2.d/K13gdm**

This renames the gdm service at runlevel 2 (the default,) replacing S (start) with K (kill), keeping it from starting. Should you ever decide to reverse it, you'd need to do the reverse:

**sudo mv /etc/rc2.d/K13gdm /etc/rc2.d/S13gdm**

---

