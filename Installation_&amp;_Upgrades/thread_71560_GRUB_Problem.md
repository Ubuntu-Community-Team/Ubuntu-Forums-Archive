---
title: "GRUB Problem"
date: 2005-10-03
forum: Installation &amp; Upgrades
---

### Post by vintendo on 2005-10-03
I get this problem with both Ubuntu and Kubuntu. After the 1st part of the installation (where u take out the disk and hit continue and it reboots) It just stays at a black screen and says GRUB. This happens everythime i install it. My copmuter is a p3 600mhz, 382MB RAM. I can get it to work on my p2 350mhz with 129mb ram. The only thing i can get to work on the p3 is Knoppix Live CD. Not even the ubuntu live cd works. Ive tried installing it on 3 different HD's and i get the same thing everytime.

---

### Post by GTvulse on 2005-10-03
What you don't tell us (and the most important part) is: Where did your install GRUB when asked to? And, what filesystem did you choose for the booting partition (root partition if you did not create a separate partition).

---

### Post by vintendo on 2005-10-03
I installed it to a HD that had XP on it. It asked me to reformat it and I said yes and I believe it put a swap and ext3. But I dont recall what I choose to boot with. I dont think I choose anything.

---

### Post by GTvulse on 2005-10-03
[QUOTE=vintendo]I installed it to a HD that had XP on it. It asked me to reformat it and I said yes and I believe it put a swap and ext3. But I dont recall what I choose to boot with. I dont think I choose anything.[/QUOTE]
Aha! Ok. This is what I  want you to do:
[list]
[*] Boot up the Ubuntu CD and type "rescue" at the booting prompt.
[*] Follow through the procedure and when asked what partition to mount choose the one with ubuntu in it. It most probably is disc0/partition1 (/dev/hda1).
[*] When you get a prompt, type ```
install-grub "(hd0)"
``` including the quote marks. Take note of the output to see if there is any error message.
[*] Type ```
reboot
``` and remove the CD from the computer.
[/list]
If everything worked out OK, you should boot into GRUB's menu.

---

### Post by vintendo on 2005-10-03
It worked! Thank you so much :p

---

### Post by furgoon on 2005-10-07
Thank you Thank you Thank you.....

Norton 2003 hosed my grub and your instructions were a savior.  Guess I should have read that ubuntu is not supported by Norton ghost.  Thanks again!

---

