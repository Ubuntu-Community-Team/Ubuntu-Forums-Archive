---
title: "Ubunti with LILO as BootLoader"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by weed-n-linux on 2008-11-15
Hello , i've set up a dual boot in my computer ( Xp and Ubuntu) , and when i turn it on , the GRUB menu appears with Ubuntu on top of the list , but i can't use my keyboard to scroll down to win xp,so i have to wait 30 seconds to get Ubuntu as my only choice,
so i thought may be this problem can be solved by installing LILO instead, but i don't know how to :( should i implement it in the .Iso file ? or install it when ubuntu is loaded ?
BTW: if anyone can provide me with a solution that doesn't require me to change the Boot loader, i will be more than delighted , my keyboard is a PS/2 not a USB , and it works well when the system is loaded.
And thanks a lot in advance .:KS

---

### Post by Mr_JMM on 2008-11-15
Can you access the bios with the keyboard?

Try pressing the num-lock key first, then the arrow keys again.

---

### Post by weed-n-linux on 2008-11-15
OMG ! i just discovered that i can't access my BIOS neither :(
i keep pressing F10 to "Enter Setup" but in vain.
Should a USB Keyboard solve my problem ? or actually a PS2toUSB adaptor for my keyboard do it ?
and i did the NumLock thing the other day...nothing neither.
thanks a lot MR_JMM for your help :)

---

### Post by Mr_JMM on 2008-11-15
Sorry for delay.

Just to confirm the keyboard is not being detected, do any of the lights come on when you press num-lock or Caps lock? (my guess is no)

How many keys does your keyboard have?

Does anything happen if your press the "e" key as if to edit the boot option?

If you have a USB keyboard around I would definitely try that.

Looking around this could be a BIOS issue but as you can't access your BIOS that's a problem. There is a setting in the BIOS that if incorrect can cause a ps2 (legacy) keyboard to be disabled by default. Hopefully you can borrow a USB keyboard to change this setting.

Failing that, you can reset the BIOS. This is normally done with a jumper clip. Check with the MB manufacturer to check if it's not obvious by looking at the MB. Caution: If you want to run windoze again you might need to reinstall some drivers. This is a last resort option only.

Sorry, I can't be of much more help.


PS Something I should have said earlier is that I don't think this is a GRUB issue so changing to Lilo wouldn't work. Also, (and this is NOT to start a discussion as many pointless threads already exist) GRUB is regarded as a better option over Lilo. Much more powerful and controllable. Stick with GRUB.

---

