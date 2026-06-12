---
title: "wierd grub 17 error fix?"
date: 2006-10-08
forum: Installation &amp; Upgrades
---

### Post by murkydurky on 2006-10-08
okay...so i was having that grub 1.5 error 17 after updating the kernel..I tried tried the xp recovery console with fixmbr and all that...didn't appear to work. i discoverd that if i just left the xp cd in the cd drive on startup, i would get to my dual boot screen (ubuntu or windows), and i can take it out once i get into xp or ubuntu. If i don't have the cd in i can't boot. :confused:  All though I am glad to be able to get back to my system again, can anyone help me fix this please? Thanks in advance

--IF this needs to be in the beginners forum I appoligize

---

### Post by nathanbriggs on 2006-10-10
17 : "Invalid device requested"

This error is returned if a device string is recognizable but does not fall under the other device errors.

post your /boot/grub/menu.lst and the output of fdsk -l and we will try and find your problem

---

