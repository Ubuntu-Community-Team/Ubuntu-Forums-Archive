---
title: "Install a configured live-USB"
date: 2011-04-23
forum: Installation &amp; Upgrades
---

### Post by Azyx on 2011-04-23
Hey. I trying 11.04 live-USB with a space to save changes on my eeepc 900. I wonder if i can install with this changes, so I don't need to do I again when I will install on my hdd? On my hdd I have separate /home/ partition.

/Cheers

---

### Post by varunendra on 2011-04-24
As far as my experience tells me, the live usb does not carry changes to the native installation. :(

It'll only install the default packages with default settings. However, you may try to create aptOnCD image to reinstall downloaded packages from it later, without downloading them again. You may face "low space in temp directory" problem if the resulting image is large, but it can be solved - I don't remember how I did it.

For carrying changes, you may try remastersys, but I haven't tried it from a live setup, so can't say how it'll behave in such case.

---

### Post by Azyx on 2011-04-26
Thanx.

---

### Post by C.S.Cameron on 2011-04-26
Remastersys works for a Live USB setup.

---

### Post by AllGamer on 2011-05-20
thanks you! 

Remastersys works great for backup and re-deployment of the same configurations on other machines

---

