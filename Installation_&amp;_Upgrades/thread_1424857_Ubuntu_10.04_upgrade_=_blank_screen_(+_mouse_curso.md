---
title: "Ubuntu 10.04 upgrade = blank screen (+ mouse cursor)"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by kevinatkins on 2010-03-08
Hi,

I've just upgraded my 9.10 installation to 10.04 Alpha 3.

Unfortunately, when I now reboot the system, instead of being presented with the login screen, I just end up at a blank screen with a mouse cursor. The 'bongo drum' login sound prompt can be heard, but there's no display.

If I switch terminals using ctrl-alt-f1 then ctrl-alt-f7, the login screen then appears. I can then select my name, enter password. The system then attempts to log me in, before returnng to the login prompt. If I try again, login is successful. This is repeatable every time - ie, login always successful on the second attempt, and every time I boot, I have to switch terminals..

I know that 10.04 is Alpha so I'm expecting a few wrinkles - I'm just curious as to what's happening and what I could do to collect information for a bug report - I don't know where to begin.

The machine itself is an IBM ThinkPad T60 with Intel graphics.

Thanks in advance,

Kevin.

---

### Post by jtso8 on 2010-03-08
All you have to do is hit the enter button and it will take you to the log in screen.  Mine does this sometimes and other times it comes up normally.

---

### Post by kevinatkins on 2010-03-09
Thanks jtso8, that does the trick as a workaround. Reading around, it would appear that's another bug to do with Plymouth, causing X to crash and restart if the enter or '2' keys are pressed... Well in any event, it's quite useful for now!

---

### Post by Topsiho on 2010-03-09
I wonder if this is related to what is said on [http://www.ubuntu.com/testing/lucid/alpha1:](http://www.ubuntu.com/testing/lucid/alpha1:) The nv driver used by default for nvidia video chipsets on the LiveCD is reported to lead to X server crashes. Investigation of this issue is ongoing and should be resolved for Lucid Alpha 2. As a workaround, users can boot with safe graphics mode" to use the vesa driver. (494627) 

Topsiho

---

### Post by rcardell on 2010-08-26
I had a similar problem but it turned out that Grub reported and used the wrong kernel, like 2.6.28 instead of 2.6.32.

You can check it by typing "uname -a"

This thread helped me: [http://ubuntuforums.org/showthread.php?t=1468589](http://ubuntuforums.org/showthread.php?t=1468589)

---

### Post by aowdnmp on 2010-08-26
I had similar problem with ATI HD 5770..every time i do a kernel upgrade, next reboot the screen goes blank..i always have to restart in safe mode, type on the terminal: "aticonfig --initial -f" that reconfigures the xorg.conf, reboot and everything works fine again.
it is a strange issue that everytime happens. maybe your problem it's similar and related to xorg.conf

---

