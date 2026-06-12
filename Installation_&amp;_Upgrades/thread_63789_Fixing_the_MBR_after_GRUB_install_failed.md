---
title: "Fixing the MBR after GRUB install failed"
date: 2005-09-09
forum: Installation &amp; Upgrades
---

### Post by wombat20 on 2005-09-09
Not a question here, but how I managed to solve my booting problems.

Through a number of installs I'd managed to get into a state where my original XP install was inaccessible and Ubuntu was booting by default, when I'd wanted dual-boot.  Reinstalling GRUB or LILO failed every time and I couldn't use apt to fix it for some reason.

Despite the dire warnings that Micro$oft give about it, I used my WinXP CD to boot into the Recovery Console and used fixmbr to, well fix my MBR.  More warnings, but I was tired and fed up so I ignored them.  The result was my MBR was put back into a state where only XP boots.  From there I was able to install BootMagic (comes with Partition Magic 8 ) and boot into either Ubuntu or Windows XP as I'd intended.      \\:D/ 

Perhaps I could've used GRUB also once the MBR was fixed, but I haven't tried that and I'm happy with BootMagic for now.

I'm not promising that fixmbr will work for everyone and you should probably back up your data (if possible!  Maybe plug your HDD into another working PC as a secondary drive?) and use it only as a last resort etc etc, but it worked for me.   :smile: 

Hope that helps.

---

### Post by GreyFox503 on 2005-09-09
Yeah, a lot of people think that if they fsck up their MBR that they need to reinstall Windows, when its actually pretty easy to just use the Recovery Console to remake the MBR.

What you could try is to follow the instructions to install GRUB, but install it to a floppy disc instead.  Then you can play with it and see if you can get the GRUB floppy to boot into both OS's.  Once you get it working, you can then install that to your regular MBR and hope your situation is fixed once and for all.

If not, then you already know what to do to fix it!   :smile:

---

