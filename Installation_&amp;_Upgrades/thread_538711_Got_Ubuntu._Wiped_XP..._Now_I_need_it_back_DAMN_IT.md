---
title: "Got Ubuntu. Wiped XP... Now I need it back DAMN IT"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by muz1 on 2007-08-30
Okay. I looked and could not find anything so here is my post.

I am running a Linux machine which was dual booted with xp but since my windows died, I stopped using it I even got rid of the install. To be honest, I had to move hard drives around so I do not know what is where. Pretty much, I really need to re-install windows but want to keep my Linux. Is there a way of backing it up, installing windows, setting up grub and then moving all the files back?

I am feeling really lost here. If I have to simply start again by installing windows and then ubuntu, is there a way of backing up my install and then simply reimporting my home folder with all of the programs and settings? Also /var/ as I am a web developer.

Any help would really be appreciated.

Thanks

muz

---

### Post by justin whitaker on 2007-08-30
> **muz1 said:**
> Okay. I looked and could not find anything so here is my post.

I am running a Linux machine which was dual booted with xp but since my windows died, I stopped using it I even got rid of the install. To be honest, I had to move hard drives around so I do not know what is where. Pretty much, I really need to re-install windows but want to keep my Linux. Is there a way of backing it up, installing windows, setting up grub and then moving all the files back?

I am feeling really lost here. If I have to simply start again by installing windows and then ubuntu, is there a way of backing up my install and then simply reimporting my home folder with all of the programs and settings? Also /var/ as I am a web developer.

Any help would really be appreciated.

Thanks

muz

If it is XP, then you can designate which partition you want XP to install on...so assuming that you have a spare partition, you can install XP to that. 

Once windows is installed, you need to reboot with the Ubuntu disc, and reinstall grub. Some good directions are here:

[http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html](http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html)

If you don't have a spare partition, then you can backup your system to CDs, DVDs, another partition, or even another harddrive. 

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

Personally, I dump everything to a USB harddrive, and then reinstall. 

Good luck!

---

### Post by deloco on 2007-08-30
Actually you can backup everything... 
In Linux you only need to burn all folders that you want to backup to a dvd, then install windows, after windows install ubuntu, and then copy all files back.

The only problem is the file-permissions... You should use the same user-name on the new install...

Also check if the hideds files are burned too...

That's it... 

I only backed up my home folder, but it should work with all other folders too...

---

### Post by HermanAB on 2007-08-30
If  Linux is working properly, then install VMware Server (or Player), Virtualbox (or Qemu) and install Windows in that. This is much better than dual booting since Windows will be running in a window concurrently with Linux.  

Also, note that Windows doesn't play well in groups.  If Linux is already installed and you would then install Windows in an effort to dual boot, it will screw up the boot record and your machine won't be able to boot Linux anymore.  This can be fixed with some difficulty but why get into that in the first place?

---

### Post by Caffeine_Junky on 2007-08-30
hey Muz,
..if ya decide to go the fresh-install rout with  ubuntu, this thread might be worth a look:  
[[COLOR="Blue"]Howto: Backup & Restore your System [/COLOR]]("http://ubuntuforums.org/showthread.php?t=81311")

Goodluck mate

---

### Post by muz1 on 2007-08-30
Hi there
I really would like to do that as  iwould really prfer to leave windows off my system.
For some strange reason, it always tells me that it will not install. 
Is there somewhere you could recommend that would step me through installing it?

Thanks for your input. I appreciate your help.

Cheers

muz

---

