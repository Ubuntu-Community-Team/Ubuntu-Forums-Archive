---
title: "ASUS 1225B - Installation attempt: no keyboard or touchpad"
date: 2012-04-15
forum: Installation &amp; Upgrades
---

### Post by slowvslow on 2012-04-15
Hi guys, 

I bought an ASUS netbook and installed Ubuntu a couple of months ago. It worked like a dream and I had no complaints. Then it got stolen. 

2GB wasn't quite enough for me so I moved to this ASUS 1225B when I got my replacement laptop. I am using a flashdrive to install Ubuntu and everything looks like it is going fine up until I get to the playpen/demo Ubuntu. At this point I cannot install any further as I have no keyboard or touch pad. 

I am a very new Ubuntu user but really want to stick with this product. Can anyone offer me some help to ameliorate this problem. 

Thanks for taking the time to read this post.

---

### Post by DylzEn on 2012-04-17
Hello. Did you find out a solution so far? I have the same problem on my ASUS 1225b, but what about the function keys? It seems like I can lower the brightness or turn off the backlight with the function keys but all the normal keys are not wotking. Anyway I didn't open a new thread because I'm trying to install a different Linux distro, not Ubuntu. Thought the solution could be the same though. Thanks to anyone who will try to help us.

---

### Post by friko90 on 2012-05-16
Did you solve this problem? My Ubuntu is already installed, but sometimes when the system is starting and i have to tape a password i can't, because i have no keyboard and touch pad. My function keys are working. Thanks for any help and sorry for my english :)

---

### Post by DylzEn on 2012-05-16
> **friko90 said:**
> Did you solve this problem? My Ubuntu is already installed, but sometimes when the system is starting and i have to tape a password i can't, because i have no keyboard and touch pad. My function keys are working. Thanks for any help and sorry for my english :)
Same thing happens to me. I managed to install Ubuntu 12.04 but the keyboard and touchpad are working randomly at every boot, that is sometimes they work normally and sometimes I can't type anything at the login screen so I have to shut my laptop down by pressing the power button. Still don't know why this happens.

---

### Post by friko90 on 2012-05-17
Did you install any other system (e.g. Windows)? Does the problem occurs only on Ubuntu?

---

### Post by DylzEn on 2012-05-17
> **friko90 said:**
> Did you install any other system (e.g. Windows)? Does the problem occurs only on Ubuntu?
Yes, both the keyboard and the touchpad work perfectly fine on Windows 7 and Windows 8 Consumer Preview. I have problems only on Mint 12 and Ubuntu 12.04, the devices have the same behaviour on these OS's, that is they sometimes work normally and sometimes they don't work at all.

---

### Post by sdenton4 on 2012-06-30
Hey, there's instructions to add the boot option:
"i8042.ignore"
at the [bug report]("https://bugs.launchpad.net/ubuntu/+bug/1014240") for this issue.  It worked like a charm for me...

---

