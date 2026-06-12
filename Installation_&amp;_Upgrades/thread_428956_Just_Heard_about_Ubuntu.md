---
title: "Just Heard about Ubuntu"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by Ameliorate on 2007-04-30
Over the weekend one of my friends showed me Ubuntu and demonstrated many of its capabilities.
After seeing this I wanted to install Ubuntu on my home computer
However, I ran into some problems: 
I need to make a partition for Ubuntu but when I use the live installer I am not sure of what I am doing.
I do not want to risk losing all of my data from XP so I need to know exactly how to install Ubuntu without any risk.
I use a Lenovo desktop computer 2.1ghz dual core 225gig hard drive 175 of which is used.
I want to create a 12 gig partition for Ubuntu but I am afraid I might accidentally erase all of my "XP data"

If anyone can give me some pointers, or a tutorial, it would be greatly appreciated.:KS

---

### Post by superyounan1 on 2007-04-30
I recommend downloading a free and open source program called "gparted". You can get it in the form of a bootable live-cd. It can do non-destructive repartitions (i dont think the included partioner with Ubuntu is non-destructive, i might be wrong).

Load the disk in your tray and boot, it should load up automatically just like the Ubuntu CD does. It will ask you some basic questions about your display adapter... when you get past all that, you want to make a 12gig ext3 partition and another 1 gig swap space partition. Then when you install Ubuntu, simply tell the installer when it asks which partitions to use for the file system (the ext3 you just made) and which to use for swap (the swap partition you just made, lol obviously).

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

Good luck buddy.

---

### Post by Bartender on 2007-04-30
Seems like the obvious thing to do is get that friend of yours to come on over and help.  Offer to buy some beer.  After installing of course.

---

### Post by superyounan1 on 2007-04-30
oh btw... plz be sure to back up the important files, assume things will go wrong!!!

---

