---
title: "SUSE screwed up GRUB!"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by afogl001 on 2010-03-19
Okay, I had Ubuntu 9.10 installed and working great.  I wanted to check out SUSE because i heard it was better for laptops and wanted to test it out.  Went through the install, which was a bit more complicated partition wise than I'd like, asking the begin and end segment shell or something.  I changed them to give me a 5GB partition, deleted an old partition of gNewSense (wireless was just too difficult to implement ie. work) and tada... stuff broke.  gNewSense still shows up in SUSE's "GRUB" but I can't boot to it.  When I threw in my 9.10 cd to fix everything, it showed that 9.10 was still installed and gNewSense was not.  

So, how can I fix this.  Is there a way to just reinstall the 9.10 GRUB for the Ubuntu I already have installed?  The sooner the better, Ubuntu was my primary OS and all my stuff is on it!  
FYI, do not recommend SUSE as far as installation goes ;(

---

### Post by zvacet on 2010-03-21
[Click!]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD")

---

### Post by phillw on 2010-03-21
> **zvacet said:**
> [Click!]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD")

A man of few words :-)

to the OP, if you're looking for a ubuntu that is less resource hungry for a laptop have a look at xubuntu and lubuntu.
xubuntu is available in 9.10, lubuntu will be available as 10.04.

It's only a few weeks before all the 10.04's come out, so now is a good time to download the betas' and try them in "Try without altering my computer" mode to see if you prefer one of them.

[https://wiki.ubuntu.com/Xubuntu](https://wiki.ubuntu.com/Xubuntu)
[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

Regards,

Phill.

---

### Post by afogl001 on 2010-03-22
Thanks for the help.  I wound up installing xubuntu 9.10 and am currently using its GRUB, but I'm going to switch it back to my Ubuntu install once I mess with openSUSE. Is there anyway to retain my Ubuntu GRUB while I mess around with installing new Linux distros (ie, so I don't have to keep repairing my GRUB when I delete the partitions I was messing around with)?  Thanks

---

### Post by afogl001 on 2010-03-27
Just as a heads up, I couldn't get GRUB installed using the supplied link (maybe because my install is on an extended partition, but who knows).  After a little more searching, I found a solution that worked for me.  Who would have guessed it would be in Ubuntu documentation.  
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

