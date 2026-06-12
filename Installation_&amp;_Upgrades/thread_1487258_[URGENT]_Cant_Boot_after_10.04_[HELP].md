---
title: "[URGENT] Cant Boot after 10.04 [HELP]"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by Eksploit on 2010-05-18
Hi guys. I just updated my Ubuntu to V10.04, and it asked to restart computer. Now everytime I start my laptop, (Im dual booting with Windows 7), I pick Ubuntu, then it just re-boots again and asks me. ANyone having this issue? Any Solutions?

---

### Post by drs305 on 2010-05-18
The best way to troubleshoot this is for you to post the results of meierfra's boot info script:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

This can be run from the LiveCD.

---

### Post by Eksploit on 2010-05-18
But I can't even get on Ubuntu..

---

### Post by drs305 on 2010-05-18
> **Eksploit said:**
> But I can't even get on Ubuntu..

You should be able to boot from the Ubuntu LiveCD. If you insert the CD and turn on your computer it should boot to the Ubuntu Desktop. If the CD doesn't boot, you may have to change the boot order in your computer's BIOS.

To do this, you have to press a key as the computer boots. Normally it is one of the function keys (F1-F12), the DEL or ESC key. Once in BIOS, change the boot order so the CD-ROM drive is the first bootable option.

---

### Post by Eksploit on 2010-05-18
Yea but I used wubi to install ubuntu?

---

### Post by drs305 on 2010-05-18
Ah!

In that case, try the fix for this bug. It is a very common problem which is easily solved if that is what is causing your problem:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")

It says 9.10 but the problem has been found with 10.04 as well.

---

