---
title: "Can't install new Ubuntu, still has remnants from Wubi that I can't get rid off"
date: 2011-02-02
forum: Installation &amp; Upgrades
---

### Post by Daanii on 2011-02-02
Being new to Linux, I first tried to use Wubi to run Ubuntu inside Windows Vista on my laptop (Compaq Presario). But I could never get that to work, so I started using a live CD to use Ubuntu. That worked well. 

Now I want to go ahead and install Ubuntu as an alternate operating system along with Windows Vista. But when grub comes up, it gives me the choice of Ubuntu, but if I choose that, it says file is corrupted. (It still looks for Wubi, I think.) Windows Vista still works fine. 

How can I get rid of that inoperable install, and install Ubuntu (non-Wubi version). I tried to do a regular install, and it seemed to work fine, but will not boot from grub. 

Any ideas? Thanks.

---

### Post by bcbc on 2011-02-02
To remove the remnants of Wubi see the [wubi guide]("https://wiki.ubuntu.com/WubiGuide#How do I manually uninstall Wubi?")

Regarding installing new - you need to boot from the CD to do a normal install (not within Windows). If that isn't working then post the [bootinfoscript]("http://bootinfoscript.sourceforge.net") and describe the issues and you'll get lots of help.

---

