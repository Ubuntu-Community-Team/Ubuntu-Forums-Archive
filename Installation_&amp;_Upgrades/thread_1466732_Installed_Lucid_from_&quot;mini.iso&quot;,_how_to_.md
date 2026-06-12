---
title: "Installed Lucid from &quot;mini.iso&quot;, how to upgrade to full system?"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by G_u_s on 2010-04-30
Hi all,

my CD burner is not reliable, and i kept having errors trying to install Lucid, so i decided to go for a network install. There was no clear info on this (i thought it would be trivial to use the network instead of the CD to copy files...), and i ended up using the mini.iso for Lucid. Now i've booted on my system, and obviously i don't have the full system.

I've found this thread ([http://ubuntuforums.org/showthread.php?t=1463991](http://ubuntuforums.org/showthread.php?t=1463991)) and this is what i'm going to do first, but i would really like to "upgrade" my system to a full, vanilla 64-bit Desktop Lucid.

Any tips?

Thanks a lot!

---

### Post by sisco311 on 2010-04-30
If memory serves, at some point of the installation you are asked if you want to install additional packages (k/x/ubuntu-desktop ...).

Anyway, just install the ubuntu-desktop package, it depends on all of the packages in the Ubuntu desktop system:
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by G_u_s on 2010-04-30
Ah, i knew there must have been an easy way. Thank you very much for your help =)

---

