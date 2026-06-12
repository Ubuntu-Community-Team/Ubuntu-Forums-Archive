---
title: "Interesting Problems.."
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by laxguy on 2008-06-11
So..I have Windows Vista on my primary harddrive, a secondary drive for movies and music (both are SATA) and i recently connected a 10 gig IDE drive to try out the new Ubuntu on. So i formatted the drive in FAT32 and had it all clean and ready to go. At this point i realized that i didn't have a DVD/CD drive, so i thought i would try mounting the ISO in daemon tools via a virtual cd drive, this appeared to work as a menu came up with a choice to go to livecd after reboot or install through windows. since i didn't actually have the physical cd, i knew a reboot into livecd wouldn't work so i chose to do the install through windows thing.

so...i chose drive H: which is the IDE 10gig sucker, and it did some little pre-install thing then told me i needed to shut down and boot into ubuntu, so i was like "ok that sounds good" i get into ubuntu and it starts to install and it takes 15 minutes or so and it says install complete and reboots my computer. only this time when i go to boot up linux it says a bunch of crap about not being able to do it because the drive is in ntfs file system. and now im like wtf, no its not..i made sure it was fat32..

then i decide to go back to the grub screen where it gives me the option to try recovery mode, which i do and i get the same error. then i decide to try to boot into Vista, and it says it won't load or something, i forget the error it gave me..right about now im about to have a heart attack cuz my computer appears dead. but i reboot and go straight into vista instead of trying ubuntu first, and it works fine. 

so my question is...why does it say it can't boot from the ntfs file system, when i know specifically i installed it on a fat32 system..

---

### Post by laxguy on 2008-06-13
no one can help me?

---

### Post by avtolle on 2008-06-13
You've run into a know issue with Wubi (how you installed Ubuntu) involving multiple drives. There is also an issue with installing under Wubi to anything other than "pure" NFTS (but I thought that was limited to newer kernels). Anyway, give me a moment and I'll get you a link to the Wubi Forum where you might find answers.

---

### Post by avtolle on 2008-06-13
[http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=234](http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=234) is the link to the Wubi Forum. Look at the FAQ sticky first; also, there will be a link there to the User's Guide, which I know discusses the multiple drive thing. HTH.

---

### Post by laxguy on 2008-06-14
thank you avtolle

---

