---
title: "ver 8.10 boot hangs after installation"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by jfarrug on 2008-11-25
I upgraded froom ver 8.03 to 8.10 and when i boot up i get the following messages

"Starting up
 Loading please wait
Gave up waiting for root device. Common problems

-Boot args (cat/proc/cmdline)
   -check root delay=(did the system wait long enough)
   -check root=(did the system wait for the right device)
-Missing modules (cat/proc/modules; ls /dev)

Alert! dev/by-uuid/31223590-a35f-45aa-a913-29849aa47faf does not exist
 Dropping to a  shell

Busybox v1.10.2 (Ubuntu 1.10.2-/ubuntu6)   built in shell (ash)
Enter help for a list of built in commands

(Initramfs)  [     33.584855] 8139 cp      0000:02:03.0  This
( id 10c:8139 rev 10) is not an 8139C+ compatible chip
  [33.584911] 8139 cp  0000:02:03.0
 try the "8139t00" drive instead

the system is halted with (initrammfs0 at the bottom.
If i then type in "Exit" the system loads with a ton of messages

I cannot figure out what is going on

---

### Post by upchucky on 2008-11-25
search for supergrub and menu.lst

your menu,list needs to be edited to see the new install

---

