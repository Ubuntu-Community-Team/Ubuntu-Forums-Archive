---
title: "Karmic grub sees osx but can't log in to it"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hananias on 2009-10-04
I have updated Ubuntu 9.10 Karmic Koala Alpha 6... Everything is pretty good!  Except now I can't go to my osx86 partition from Grub 1.97 beta (grub2).  I see it, but when I click on the highlighted partition... it seems as if grub resets (just for a blink of an eye it goes black, then grub is up again)... but no matter what I hit, I can't access that partition!  If I want to log to my osx86, I have to change my partition order in the motherboards boot up option to the osx86 partition.  In the osx86 boot loader, I can't access Linux...:confused:

so this is a very frustrating situation.  I really have to think carefully which OS I need before I boot up the machine, and go through the trouble of changing the Boot process.  Painfully slow... Please any help, maybe with fixing grub.

---

### Post by hananias on 2009-10-05
Anybody please?  Or is there a place I can go for Karmic help?  Thanks in advance.

---

### Post by drs305 on 2009-10-05
It's not specific to your problem, but I wrote an introduction to Grub 2 explaining how it works, and there is also the G2 wiki:

GRUB 2 BASICS  / GRUB 2 WIKI
[Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")
[https://wiki.ubuntu.com/Grub2]("https://wiki.ubuntu.com/Grub2")

You can look at /boot/grub/grub.cfg (or hit E after selecting it on boot) to see what settings Grub 2 is using to try to boot into your osx.

---

### Post by hananias on 2009-10-05
Maybe my wording in the original thread was off... I couldn't think of the correct vocabulary, but it came back to me!

My problem is with grub 2, it sees my osx86 drive.  I just can't click on it, it just ignores my clicks.  So in order to boot into osx86 I have to go in the BIOS. Change boot order in BIOS to boot to osx86 HDD.  

I have never been good with boot loaders, but I use to have Jaunty & osx86 working.  But deleted it, too many glitches!  I wanted to give Karmic a try, and so far I like what I see.  But now I can't access my different OS's under one boot loader!  Help please.

---

### Post by DGortze380 on 2009-10-05
To the best of my knowledge, grub does not support OS X because OS X uses a different method of boot strapping.

If you're on an Apple, use rEFIt or yaboot accordingly.

If not, you're in violation of Apple's EULA by running OS X and we can't provide assistance on this forum.

---

