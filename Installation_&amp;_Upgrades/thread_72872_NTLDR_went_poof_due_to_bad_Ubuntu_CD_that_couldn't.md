---
title: "NTLDR went poof due to bad Ubuntu CD that couldn't complete install!"
date: 2005-10-07
forum: Installation &amp; Upgrades
---

### Post by Niomi on 2005-10-07
Eeeks :P
Okay, so, smooth move on my part, I scratched my Hoary CD (Hoary is VERY spiffy by the way!!) and didn't notice untill the installer complained about a bad CD. So I shut down the PC because it was really warm in the room due to the multiple computers (stupid, stupid, STUPID!! it TOLD me it would be unstable!! GRAH!!)

So both of my hard disks had intalls of XP, the first disk had an older install that I no longer needed and I was going to wipe it in favor of Ubuntu. The second disk has XP on it, which I _NEED_ to keep because some important work-related pages require active-x.  I had the system booting on the first disk with the old XP on it. I didn't have Ubuntu touch the second disk, but it wiped the first and didn't install completely because of the bad disk. I burned a new disk and ubuntu is now running (woohoo! look, ma, no windows! *wriggle*) I need to figure out how to get NTLDR back, and then get GRUB to work with it, or something to that effect. Preferably without wiping or severely displacing my XP or Ubuntu systems.

I apologise for this post which is undoubtably very mispelled and rambly. I'm still working on getting firefox built up with my favorite extensions (including spellbound!). Thanks for helping me out! :D

---

### Post by kondor on 2005-10-09
Search the forum for GRUB configuration and check the WIKI.

Since WinXP is gone from drive hda (sda), the NTLDR is a moot point. It is inoperative without a BOOT.ini and that is not there cause WinXP has been replaced by Ubuntu.

GRUB will now do what NTLDR did. I'm surprised that the GRUB configuration during install didn't show the hdb (sdb) with theNTFS partition. I am new to Ubuntu.

If you wanted WinXP doing the booting, a Rescue tussle on the WinXP drive might allow you to boot from there (NTLDR) if it is a SATA. Either way, you'll have to write some config files anew.

If you insist on WinXP doing the booting, and they are PATA drives, I think you'll need to swap them, getting the WinXP to the master position. Doing GRUB properly would probably be easiest. If SATA, I think you'd still have to switch cables to get WinXP up first as the BIOS of mine follows the MB order - 0,1,2,3

You should find what you need with a quick search. I've done mine all the easy way. WinXP on sda, Linux XX on sdb, GRUB to MBR on sda.

But, The first drive is kaput as far as Windows is concerned. It will be GRUB there for booting I think.

---

### Post by SilentCacophony on 2005-10-09
Hi. As kondor mentioned, grub should work just fine as a boot menu. Generally it automatically sets up correctly.

If you check your */boot/grub/menu.lst* file, it should have put an entry for Windows XP, but if it didn't, you can add one. With XP being on the second drive, you'd generally need to *map* the drives around to make it happy about that. I'd add this to the end of the file:

```
title Windows XP
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1
```

---

