---
title: "Need to Re-Install Grub"
date: 2004-12-16
forum: Installation &amp; Upgrades
---

### Post by Thanatos9602 on 2004-12-16
Do to the local phone company screwing with my DSL setup, I had to reboot Win98SE. I still have a good copy of damnsmall on one drive & Ubuntu on another. How can I reinstall GRUB? Without reinstalling Ubuntu. I have tried thru the live & the install cd. Both give me trouble with the partition that damnsmall is on. I guess they don't like each other. Neither disk will install grub. Remember, although I'm a pro at computers, I'm a newborn at linux. I get lost easy. Is there any way to install it from windows?? Might be a stupid question, but thought I'd ask. Thanks for any time, trouble & help. :sad:

---

### Post by Thanatos9602 on 2004-12-17
OK, I reinstalled DamnSmallLinux, told it not to install LILO, then installed Ubuntu. Having a full time DSL internet hookup makes it a trip to install. Problem is, Ubuntu won't notice DamnSmall. So I reinstall DamnSmall & it won't notice Ubuntu. Without DSL I had both on here no problem with GRUB for a loader. Do I need to disconnect DSL & reinstall them both to be able to use them both?? This is getting confusing.:confused:  Is it possible to have both fully installed on the machine?? Thanks.:?:

---

### Post by adbak on 2004-12-17
I don't think that you need to reinstall them.  I think that if you edit the file /boot/grub/menu.lst you should be able to add DSL (as long as you know what partition(s) it's on) without having to reinstall anything.  As far as what to add, I have no clue what it would be, but perhaps you could Google it ( [http://www.google.com/linux](http://www.google.com/linux) ).

---

