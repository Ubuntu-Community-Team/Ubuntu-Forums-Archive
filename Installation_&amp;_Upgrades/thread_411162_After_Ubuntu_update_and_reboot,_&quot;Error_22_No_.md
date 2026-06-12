---
title: "After Ubuntu update and reboot, &quot;Error 22: No such partition&quot;"
date: 2007-04-16
forum: Installation &amp; Upgrades
---

### Post by monaleilani on 2007-04-16
I did some updates on an laptop loaded with EE, and afterwards Ubuntu asked me to reboot. I guess the kernel got updated; I didn't look too hard at the Update list. Anyway, I just shut down the laptop and when I turned it on this morning, I got the lovely message of Error 22: No such partition found. 
Is this something easy to fix? Do I just need to tell Grub to point somewhere else?

---

### Post by blamecanada on 2007-04-16
Sounds like your menu.lst file is directing grub to the wrong place, perhaps you can post your  file?

---

### Post by monaleilani on 2007-04-16
::groan:: I'm not sure how to do that unless to I can locate my Ubuntu install disk and run the live OS... Which is somewhere in this room, I hope. I'll try to find it and get the menu.lst file posted.

---

### Post by blamecanada on 2007-04-16
Yea, Live CD is about your only option atm unfortunately.

---

### Post by reiki on 2007-04-16
When Grub gets to the menu list, highlight what appears to be the new kernel entry, hit "e" on your keyboard (to [e]dit that entry) and take a look at where it's pointing. If it's pointing to the wrong partition... edit it, and tehn hit "b" ( to [b]oot ) with the edited entry.

THIS WILL NOT change the grub menu.list. It just gives you a chance to alter it for this boot only. Once you get to a working kernel you can edit the file permanently.

You could also try booting an older kernel if it's in the list

---

