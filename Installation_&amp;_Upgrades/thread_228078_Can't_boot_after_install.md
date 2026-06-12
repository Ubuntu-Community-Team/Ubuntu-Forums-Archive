---
title: "Can't boot after install"
date: 2006-08-02
forum: Installation &amp; Upgrades
---

### Post by kvalis on 2006-08-02
Just downloaded desktop 6.06. Tried out Live CD and went for installation. When I boot the Ubuntu logo comes up, then it stops booting after *Waiting for root file system.*

After a couple of minutes it drops to
 a shell and the line:

*/bin/sh: can't access tty; job control turned off.*

Let me mention that PCLinuxOS was installed on the PC before this install, but I chose to use the whole disk for Ubuntu when prompted for this. 

Any suggestions woild be welcome. And do remember that I am a newbie!

---

### Post by leetwanker on 2006-08-02
What are the chances that your linux hard drive is plugged into an it8212 IDE controller?

If this is the case: the easiest option is to move onto a distro that supports your hardware. Option B is to plug your linux drive into a regular IDE controller on your mobo that doesn't need a driver that Ubuntu doesn't support, reinstall Ubuntu, compile a custom kernel with it8212 support, switch the drive back to the it8212 controller, reinstall grub (somehow), and pray that all this worked.

I didn't feel that it was worth this much trouble to me. This however is a well documented issue that you'll see lots of people complaining about and Ubuntu doesn't seem to put alot of effort into fixing.

Good Luck.
wanker

---

### Post by leetwanker on 2006-08-02
by the way, here's a link to my post:

[http://www.ubuntuforums.org/showthread.php?t=227517](http://www.ubuntuforums.org/showthread.php?t=227517)

I'm back to using SuSE 10.1 which has its own set of problems, but atleast it boots.

---

### Post by kvalis on 2006-08-03
Did not have time to wait around for a solution.  Installed Freespire to see if that would work with my wireless card, and it did eventually, but too many configuration hickups.

Had a Ububtu install CD ver. 5.10, installed that over Freespire, and my DLink wifi card started working immediately after reboot.

Happy as a lark, I then updated to 6.06 via internet, it took a couple of hours, and that worked a treat.

Unfortunately, my wifi card does not work since reboot - but I will post that problem separately.

Thanks for suggestions

kvalis

---

### Post by leetwanker on 2006-08-03
kvalis: do you have the IDE/Raid controller that I guessed you did?

---

### Post by kvalis on 2006-08-04
Leetwanker

The IDE controller is a 82801DB (ICH4) IDE Controller.
Thanks for your help. A bit confusing for me as a newbie - but grateful for the suggestion.

kvalis

---

