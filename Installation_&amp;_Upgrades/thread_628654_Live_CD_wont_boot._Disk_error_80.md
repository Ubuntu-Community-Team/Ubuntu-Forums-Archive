---
title: "Live CD wont boot. Disk error 80"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by Aspra on 2007-12-01
I have an old HP desktop that i want to put Ubuntu, Kubuntu, or Xbuntu on but im getting this -
   [B]Loading /casper/vmlinuz..............isolinux: Disk error 80, AX = 4200, drive 9F
   Boot failed: press a key to retry...[/B] and its the same for all of them.


   I have tried Ubuntu 6.06/ 7.04/ 7.10, Kubuntu and Xbuntu, all at different burn speeds and it still wont boot. I put in two different hardrive and swapped around the two old roms the computer came with. I even installed windows XP on it to see if it would even work before i tried putting Ubuntu in again, worked fine and installed fine. The funny thing is Ubuntu used to run on this machine and then one day it just wouldn't boot again. that was a few months ago. But since XP installed fine i have no idea why its not working.

Thanks for the help.

---

### Post by meierfra on 2007-12-01
I'm not sure it is the same problem, but you might check out this thread:

[http://ubuntuforums.org/showthread.php?t=622850]("http://ubuntuforums.org/showthread.php?t=622850")

---

### Post by Pumalite on 2007-12-01
DBan your drive: [http://dban.sourceforge.net/](http://dban.sourceforge.net/)
Then use Gparted Live CD to make a large partition of your whole drive formatted ext3 (they'll tell you is not necessary, but believe me: it is)
Then install Ubuntu.

---

### Post by meierfra on 2007-12-01
Pumalite might be right (he usually is) but I still would check the cables and the bios setting  first as suggested in the link I provided.

---

### Post by Pumalite on 2007-12-01
Checking cables and connections never hurt anyone. (I hope)

---

### Post by Aspra on 2007-12-01
Its something really odd wrong with that computer. I have Windows running on it right now- just installed it yesterday. working perfectly. But when I try to even run a Live CD, not even install ubuntu it wont boot. nothing. so ill try Pumalite's suggestion, and i guess recheck everything. ill let you know if it works.
 Thanks.

---

