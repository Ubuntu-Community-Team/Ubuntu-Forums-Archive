---
title: "so if i install ubuntu will it automatically dual-boot?"
date: 2006-11-27
forum: Installation &amp; Upgrades
---

### Post by dmber on 2006-11-27
I run XP on my computer.  I just want to install ubuntu and have it so when i start up my computer it asks me which one i want to run.  i read them "howto: dual boot" thread but there were like 50 different ways to do it and it didn't seem like there was a consensus as to how to do it.

do i just go through the installation from the live cd, re-partition some space on my hdd and it'll be good to go -- as far as dual-booting?

thanks a lot!

---

### Post by damonw5 on 2006-11-27
The Ubuntu installer is pretty good about detecting your windows partition and putting it in GRUB (the menu you see when you first turn on your computer). It's Windows that likes to take over the whole system when it is installed!

So my advice is to go ahead and install Ubuntu. Then when you start up your computer, you will have a choice between Ubuntu and Windows (you may need to press ESC to see the menu, though).

---

### Post by dmber on 2006-11-27
thank you for your reply.  here's my new problem.  i'm following this [graphical install instruction page]("http://www.psychocats.net/ubuntu/installing") and when i get to "prepare disk space" my choices are different from the ones on the guide.  i have these three choices:

1. Erase Entire disk:IDE1 master (hda) - 120.0 GB WDC ....
2. Use the largest continuous free space
3. Manually edit partition table.

I definitely don't want to do option #1, because i want to keep my windows partition.  Should I do number two?  When I go in to manually edit the partition table I get this (picture):

[IMG]http://img462.imageshack.us/my.php?image=dscn1775bu2.jpg[/IMG]

which option should i use?  how do i go about this?

thanks a lot for your help!

---

### Post by dmber on 2006-11-27
it doesn't seem like the screenshot is coming up.  here's a different link:

[http://img463.imageshack.us/img463/553/dscn1775bv7.jpg](http://img463.imageshack.us/img463/553/dscn1775bv7.jpg)

---

### Post by styven on 2006-11-27
Use no. 2

Steve

---

### Post by dmber on 2006-11-27
> **styven said:**
> Use no. 2

Steve
thanks.  will it use up the "unallocated" portion?  i don't want to lose those 50 gigs, and it seems like that's what's going on...

---

