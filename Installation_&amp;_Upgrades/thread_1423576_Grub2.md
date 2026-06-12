---
title: "Grub2?"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by helblaze on 2010-03-06
I was wondering how I can get Chainload into Grub2 to show up as an entry in Grub, I just installed Karmic a week ago on my laptop.

I want to set Grub to use this [theme]("http://gnome-look.org/content/show.php/Ubuntu+Radience+for+Grub+2+%5BBURG%5D?content=121105")

I'm using a netbook, how would I change grub's resolution to 1024x600.

---

### Post by helblaze on 2010-03-07
bump

---

### Post by uRock on 2010-03-07
From reading that page, I would say it isn't working. Have you tried the instructions on the page?

---

### Post by helblaze on 2010-03-07
I haven't even gotten to the point to install the theme yet

I am still in Grub Legacy, I don't get how to get the Chainload into Grub2.

I understand how to install the theme by the way.

---

### Post by uRock on 2010-03-07
Did you upgrade from jaunty?

---

### Post by uRock on 2010-03-07
This [link]("https://wiki.ubuntu.com/Grub2") will walk you through upgrading from grub 1.5 to grub2 aka 1.97beta.

---

### Post by helblaze on 2010-03-08
no I didn't upgrade, installed linux for the first time on my netbook, and I already have 1.97beta, but I don't have the Chainload into Grub 2 option, and I don't know how to get that. (I would rather test it out before I do an actual upgrade)

---

### Post by helblaze on 2010-03-08
bump, I would like to get this solved asap.

---

### Post by adam814 on 2010-03-08
If you already have GRUB version 1.97beta that *is* GRUB2.  It would seem kinda pointless to me to have GRUB2 chainload itself.

I believe Karmic installs GRUB2 by default on new installs (which yours is).  If you upgraded from an older version of Ubuntu that originally used legacy GRUB and you decided to install GRUB2 you'd get an option to chainload into it from legacy GRUB to make sure it worked before removing your old bootloader.

---

