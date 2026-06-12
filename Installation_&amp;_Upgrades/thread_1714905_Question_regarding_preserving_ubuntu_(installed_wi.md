---
title: "Question regarding preserving ubuntu (installed with wubi) after formatting Windows 7"
date: 2011-03-26
forum: Installation &amp; Upgrades
---

### Post by smukherjee11 on 2011-03-26
Hello. I have installed Ubuntu on my laptop about a month ago using Wubi, and the laptop came with Windows 7 Home Basic already installed. Ubuntu is installed in another partition (E: ) on my Hard Disk.

If, for some reason, I have to format the Windows partition (C: ), then I'll lose access to Ubuntu right? Probably since the Windows bootloader, after formatting C: won't know about the Ubuntu installation, right? In that case, what should I do so that I don't lose access to Ubuntu even after a fresh installation of Windows 7 ?

Thanks in advance.

---

### Post by bcbc on 2011-03-26
If E: remains untouched you can manually add back an Ubuntu entry to the boot manager (using bcdedit or easybcd) and copy E:\ubuntu\winboot\wubildr to C:\

but it's easier to copy the root.disk outside of the E:\ubuntu directory or rename the whole thing to E:\ubuntuSave. Then you're done replacing Windows, reinstall Wubi (with a 3GB size - smallest) and after the Windows part is completed (before rebooting) just rename delete E:\ubuntu and renamed E:\ubuntusave to E:\ubuntu

If you're going to the trouble of reinstalling Windows, you might consider [migrating]("http://ubuntuforums.org/showthread.php?t=1519354") Ubuntu to its own partition instead of reinstalling Wubi.

---

### Post by smukherjee11 on 2011-03-28
Sorry for the late reply. I tried it yesterday and it works! Thanks a lot, bcbc.

I have, for now, used the "copy over root.disk and the ubuntu folder" trick mentioned in the previous post. Regarding migration, I'd like to know more. Can someone explain it to me, and/or provide me links to where I can learn more about it?

---

### Post by millertime on 2011-03-29
I just formatted windows 7 and the boot manager automatically detected Ubuntu after the fresh install, I am really curious into how this works, does the boot manager save a config file the 100mb system reserved partition windows uses. 

Feels odd asking a windows questions on the Ubuntu forums.

I know I should still install wubi again and rename the ubuntu folder as described. But it is kind of weird it has been auto detected.

---

### Post by smukherjee11 on 2011-03-29
Is that so? In my case, however, after the fresh install of windows 7, Ubuntu appeared in the boot menu only after I ran wubi and it asked me to reboot. I replaced the \ubuntu folder with my old one before rebooting (just as said by bcbc), and rebooted, and bingo. It was there in the windows boot loader, and booted into Ubuntu as if it was always there.

From what I think, wubi writes a new boot entry to Ubuntu in the windows boot.ini, which in turn, loads the Grub bootloader and subsequently ubuntu. But millertime, are you sure you didn't run wubi on the clean install of windows 7, and the Ubuntu option appeared in the bootloader?

---

### Post by bcbc on 2011-03-29
Wubi either creates an entry in boot.ini for XP or BCD for vista/7. It's shows a menu option and points at the wubildr.mbr file. (In XP this is C:\wubildr.mbr, and in Vista/7 it's on the drive you installed Wubi to i.e. x:\ubuntu\winboot\wubildr.mrb)

Windows does not detect wubi. So for whatever reason, for *millertime*, the boot manager entry was not cleared during the reinstall (I know Windows 7 tends to use a separate boot partition, and this may be the reason).

---

### Post by smukherjee11 on 2011-03-29
I get it now, thanks a lot.

By the way, does "migrating" mean creating a dedicated partition for ubuntu, formatted with the ext4 filesystem? For that, a raw partition is required, right? And if that is the case, will the Windows bootloader be deleted? 

I am asking because I had done an Ubuntu install by booting from the CD directly on another machine running Windows XP(the raw space for ubuntu was made before doing this), and it only kept the Grub bootloader. And when I decided to make a swap partition for Ubuntu, I resized another partition from within Windows, a _big_ mistake on my part, and I lost access to Windows and Ubuntu completely, and was unable to recover Grub. In the end, I had to reinstall Windows XP on top of the Ubuntu partition by reformatting it, and delete the old XP :(

Due to this, I've been afraid of only using the Grub bootloader  :P

---

