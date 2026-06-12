---
title: "Uninstall Ubuntu"
date: 2006-03-04
forum: Installation &amp; Upgrades
---

### Post by nielsrondou on 2006-03-04
hi,
I wanted to remove Ubuntu from my laptop so I removed the partition where it was installed to. 
Now when I reboot my pc, I get error 22 when GRUB is loading...
Can anyone help me how to remove this GRUB-error so I can just boot my winXP again?
I found out that I have to type "fdisk /mbr", but I have no floppy-drive on my laptop...
thx for the help!

---

### Post by bluesman on 2006-03-04
Hi, 
boot your Windows Installation CD, but instead of Installation, choose Recovery Console, and then type fixmbr (or mbrfix - I don't rememeber exactly - but you can use "help" for commands) and that should do it.

---

### Post by nielsrondou on 2006-03-04
yes!! it worked!!
the command was "fixmbr" btw...
thanks a lot!

---

