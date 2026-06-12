---
title: "dual boot"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by don3390 on 2007-03-26
I have went over all the post about dual booting and either I'm missing an answer or don't understand( could be both.My   problem is this-I have two HD SATA One is 250 gig the other is 120 gig. I have XP on the 250 drive and put Ubuntu 6.06 on the 120. When I boot up all I get it windows xp. If I go in and switch the hd leads it boots up to ubuntu. Do I need to go back and renistall ubuntu I tried doing it in bios didn't work. SATA drives makes my head hurts.
  I am very new at linux but love what I see. Guess it's my 72 yr old brain is slow. Thanks for a simple answer if possible.

---

### Post by confused57 on 2007-03-26
> **don3390 said:**
> I have went over all the post about dual booting and either I'm missing an answer or don't understand( could be both.My   problem is this-I have two HD SATA One is 250 gig the other is 120 gig. I have XP on the 250 drive and put Ubuntu 6.06 on the 120. When I boot up all I get it windows xp. If I go in and switch the hd leads it boots up to ubuntu. Do I need to go back and renistall ubuntu I tried doing it in bios didn't work. SATA drives makes my head hurts.
  I am very new at linux but love what I see. Guess it's my 72 yr old brain is slow. Thanks for a simple answer if possible.

You might just need to add an entry to boot Windows to your /boot/grub/menu.lst:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

You mentioned switching leads to get Ubuntu to boot, I suppose you mean connecting your drive with Ubuntu to the SATA#1 controller...if this is the case, you should be good to go.

---

### Post by BrianK on 2007-03-26
As far as I know, the answer isn't simple.  If this is a new Ubuntu install, you might consider reinstalling.  When you install the second time, be sure both hard drives are plugged in & that the machine boots into windows.  If that's the case, when you install, be sure not to install ubuntu on the windows hard drive (it should tell you which is which) & then ubuntu will install a bootloader (probably on the windows drive) that will boot either Ubuntu or Windows.

To fix your current setup, you'd have to add a new entry to grub which is non-trivial.

edited to add: confused57 suggestion is what I was referring to as non-trivial.  It will work.. be brave.  It's not *that* hard.  ;)

---

### Post by don3390 on 2007-03-27
Thanks to everyone for your quick answers. I renistalled and all is well. I must say I have been in a number of other forums on the internet and never had the help coming so quick. Now if someone could tell me how to us flightsim 2004 on ubuntu I could get xp off my computer. I can use X-Plane  flight sim though. Again thanks alot:guitar:

---

