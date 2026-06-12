---
title: "System only boots via floppy/cd after Dapper install"
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by crossedout on 2006-06-17
Hello all,
I am a fresh noob to ubuntu and linux in general.  However, I did my homework before installing Dapper and spent alot of time reading posts, guides etc so as to limit any errors.  Having said that, I performed a dual-boot install with winxp and everything went well..with one exception.  The only way I can boot my system is to use the floppy or cd drive.
I installed GRUB to floopy so as to keep it from installing in MBR, I also copied/editted the necessary boot.ini file in win to make sure both OS would be listed.  All of that works fine too.

The problem occurs at startup, the system needs my grub floppy or an install cd , if it doesn't get it, I simply get a message of "press F1 to retry, or F2 for Setup".  Well neither do me any good.  I of course insert the floppy and the GRUB boot menu appears where I can then choose which OS to use, while choosing win, takes me to the win boot menu where I can choose again what OS I want to load.
I guess my question is, how can I get my system to boot from the hd and ignore that GRUB menu so it shoots directly to the win boot menu?
After reading many posts, I'm assuming an edit to the menu.lst might solve it.  I have no problem learning but as I said am VERY new to all of this and would hate to destroy something after painstakingly setting it all up fairly accurate, and to be honest I am about burnt out from all the trial and error.

Sorry for such a lenghty post, any help is appreciated. Thanks!

---

### Post by rcarring on 2006-06-17
If you want to use the bootloader on the hard disk (ntldr) then you may have to install grub to the mbr and let it take on the role of main bootloader. XP won't know what to load otherwise.

---

### Post by crossedout on 2006-06-17
@rcarring: Thanks for the suggestion, however I get the same result.  My system refuses to boot from the hd.  I am still left with having to use a cd or floppy to gain access to any part of my system (ubuntu or otherwise).
I'll keep poking around and hopefully stumble upon something or maybe someone else will have another idea.

---

### Post by confused57 on 2006-06-17
Maybe this will help:

[http://www.ubuntuforums.org/showthread.php?t=188819&highlight=floppy](http://www.ubuntuforums.org/showthread.php?t=188819&highlight=floppy)

---

