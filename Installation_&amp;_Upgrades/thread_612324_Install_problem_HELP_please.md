---
title: "Install problem HELP please"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by jakari on 2007-11-13
iv just got my ubuntu 7.10 disks in the post and i put the disk in and boot it up and get the menu where it wants me to pick what i want to do, boot normal, boot grpahics safe mode or what ever

and i go to run the first one what ever it says, to run ubuntu and i get this...

[	0.404000] ..MP-BIOS bug: 8254 timer not connected to I0-APIC
[	0.408000] Kernel panic - not syncing: I0-APIC + timer doesn't work! Boot with
apic=debug and send report. Then try booting with "noapic" option.


can anyone tell me whats rong and how to "Boot with
apic=debug" and how to do the "noapic" option???

thanks

---

### Post by jakari on 2007-11-13
can anyone help me please, i really want to install ubuntu, never use it before and it looks cool :)

---

### Post by lonniehenry on 2007-11-13
Jakari   boot up and when the menu comes up, highlight the first choice and hit e.  hightlight the line that has the word splash in it and type noapic at the end of that line. Hit b to boot.  If that works and you are able to boot okay, then after you do the install you can make it permanant by editing grub menu.lst.

---

### Post by lonniehenry on 2007-11-13
Oops You havent installed yet so you hit f6 and type noapic and enter. use my first answer if you get it installed and can't boot.  sorry about steering you wrong.

---

### Post by jakari on 2007-11-13
ok il try that now :)

---

### Post by jakari on 2007-11-13
wooo it worked.... ok maybe notit now gets to the ubuntu loading screen the one with the bar going from side to side and stoppes on it

---

### Post by confused57 on 2007-11-13
> **jakari said:**
> wooo it worked.... ok maybe notit now gets to the ubuntu loading screen the one with the bar going from side to side and stoppes on it
You might be able to determine what's causing the problem by removing "quiet" and "splash", when you press F6 and add noapic...make a note of any error messages that might be displayed.

---

