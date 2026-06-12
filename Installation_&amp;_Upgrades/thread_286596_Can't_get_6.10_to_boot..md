---
title: "Can't get 6.10 to boot."
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by Captain Emo on 2006-10-27
I tried both the desktop CD and the Alternate CD on my Dell Optiplex G1.  It has a Pentium II 400mhz, and 256mb RAM and a Rage 128.

I boot the CD, then it stops at the Ubuntu logo screen.  I can't figure out what is wrong, because I put it in my notebook.  Comqaq Armada M700, and its installing right now just fine.  Pentium III 733mhz, 128mb RAM, and a RAGE Mobility.

Should I try 6.06, or Xubuntu even?  Or what should I do to get Edgy to actually boot.

---

### Post by vibestriton on 2006-10-28
Did you try safe mode?

Or it might be this...
[https://launchpad.net/distros/ubuntu/+source/wvdial/+bug/50041](https://launchpad.net/distros/ubuntu/+source/wvdial/+bug/50041)

Can you get any log info on the error?  

If all else fails, yeah, it may be worth giving dapper a shot.

---

### Post by Captain Emo on 2006-10-28
I couldn't do anything.  It showed the Ubuntu logo at the top of the screen.  And it stops there.  With the Alternate CD its supposed to give you install options I didn't even get that far.

---

### Post by rlozano on 2006-10-28
i would assume that you are using a radeon video card.

this is normally the problem for those who are using ati/radeon video card. i just cant figure out why ubuntu/kubuntu cant work well for some radeon cards.

try adding vga=791 in the grub boot line. it may hell you to continue. if it works, then you have the chance to configure your rage properly.

---

