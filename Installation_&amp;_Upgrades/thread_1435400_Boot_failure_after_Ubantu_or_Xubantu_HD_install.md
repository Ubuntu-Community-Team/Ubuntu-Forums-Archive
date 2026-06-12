---
title: "Boot failure after Ubantu or Xubantu HD install"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by newpaul on 2010-03-21
Help requested...
 
When I install either desktop version of Ubuntu 9.10 or Xubantu 9.10 it boots ok when ask to reboot at the end of the install, but will not reboot after that (2nd attempt and all after fail)
 
On 2nd and later attempts the grub menu comes up and I choose default Ubantu and the Ubuntu circle logo displays for about 30 seconds, and most of time I see it try to access my floppy drive (sometimes the floppy drive light stays on, sometimes it does not) a cursor then blinks in the upper left hand corner for about 10 seconds and then the screen goes blank and freezes there until I power down.
 
My System
Dell Dimension 2350
Celeron 1.80 G Hz
768 Meg RAM
30 Gig hard drive
 
 
Note: Xubantu installs OK to HD on another system I have, but not on this Dell. To test the Dell I did install Puppy Linux with default grub loader to HD ant it works OK (boots OK to HD each time).
 
 
Side note: At first I tried this Dell to set up dual boot with XP and Ubantu and same symptoms Ubantu only booting OK once and then never again so I thought it was dual boot issue so I deleted all partions (XP is now gone) with latest GParted version and attempted installing Ubuntu 9.10 and then Xubanto 9.10 on the whole harddrive but still no boot past the first time
 
I though this might not be a grub issue since it seems to get past grub and the Ubantu circle shows for about 30 seconds before the system freezes. only a guess on my part as I don't know enough about Grub or Ubuntu to troubleshoot without help.
 
I see I can hit "e" to get to the grub editor and I looked at the grub boot code but don't know enough about it to edit for a fix..
 
I thought about Lilo but did not see an option on the normal Xbuntu ,or even when I used the alternate install CD,for a Lilo option.
 
Also note I can run the live CDs for Ubuntu and Xubuntu OK on this Dell. Only HD install gives me problems.
 
 
any and all help and replies appreciated.

---

### Post by newpaul on 2010-03-21
haven't seen any responses yet.

please let me know if you have any suggestions or ideas to aid or resolve

Thanks

---

### Post by newpaul on 2010-03-21
I found the fix...

here..in the dell support ubuntu foruml 


[http://ubuntuforums.org/showthread.php?t=1334658](http://ubuntuforums.org/showthread.php?t=1334658)

see post number 6


boots fine now, time after time



hope this helps others with same issue

---

