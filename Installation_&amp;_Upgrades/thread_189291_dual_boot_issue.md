---
title: "dual boot issue"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by bhanja_Trinanjan on 2006-06-05
Hi!
  I had Windows XP 32 bit and 64 bit on my 1st hard drive. After I installed Ubuntu 6.06 on the free unpartitioned space on the 1st hdd, GRUB recognized both Windows installations. But I was unable to boot into either.
I got the error 'Cannot find <windows-root>/system32/ntoskrnl.exe' (Don't remember the exact path) So, both my Windows installs were screwed up. Next, I did a fixmbr in vain. After that, I installed a 3rd copy of Windows to a different folder on the hdd and backed up the contents of my 1st hdd to the 2nd and 3rd hdds. Then, I did a low level format of my 1st HDD and installed XP 64 bit. Now I want to install Ubuntu on the free space on the 1st hdd and successfully boot to Windows.

1) How can I prevent dual boot problems?
2) How do I back up and restore my Windows MBR in case of trouble?
3) Why did my previous install run into dual boot problems?

 Please help, I am a newbie and need detailed help!

---

### Post by cotcot on 2006-06-05
to 1. :  you could install the grub bootloader to another place than the MBR (removable media for instance). I have it on a floppy. Floppy out is XP; floppy in ubuntu grub loader. Reply no if ubuntu install asks you to install the bootloader in the MBR. You then get the question where to put it : in my case it is /dev/fd0 for the floppy. Afterwards you have to make the windows partition active again. You could use fdisk for that.

to 2.  :  read this : [http://freshmeat.net/articles/view/1375/]("http://freshmeat.net/articles/view/1375/"). The command you are looking after is in Part 1 : dd if ...

to 3.  : sorry  no idea

---

