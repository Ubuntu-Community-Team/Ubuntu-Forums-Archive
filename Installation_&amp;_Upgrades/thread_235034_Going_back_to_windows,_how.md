---
title: "Going back to windows, how?"
date: 2006-08-12
forum: Installation &amp; Upgrades
---

### Post by Hyuuga on 2006-08-12
Sorry but since a dual boot is near-impossible i've decided to go back to windows. Not because i like it in any way, but because my laptop won't work well with it. The problem is i haven't gotten any system backups to restore and the very annoying GRUB loader just won't boot to my windows XP home edition CD. I don't have a 6.06 install cd, only 5.1, and i used the partinioning step of this one to format everything to a single FAT32 partition. It shouldn't have left anything behind, but the goddamn GRUB loader is still there and won't let me boot to my winXP cd.

IF this is more fit in the 5.1 section then move it.

THe question is, how the heck to i get it to boot the damn winXP cd so that i can install winXP again?
what must i do? all i have left on the machine is the loading screen with its boot options (i've tried specifying it to boot from CD-rom with no luck) and the damn grub saying "grub loading stage1.5, grub loading please wait... error 17".
Even if it means install 5.1 and then upgrading all over again, tell me what the heck to do!

---

### Post by VirtuAlex on 2006-08-12
if you're able to boot into 5.1 cd but not into xp cd, that means something wrong with your xp cd.

---

### Post by Nathaniel on 2006-08-12
First off, GRUB has nothing to do with booting CDs. Booting from CD is probably turned off in your BIOS settings, or the HDD has higher priority. Try checking these settings.

As for Windows and the MBR, when you manage to boot from the Windows CD, go into the System Restore section, until you get to a DOS-like prompt. Enter "fdisk /mbr" or "fixmbr", and it should replace GRUB with the Windows own boot-loader.

---

### Post by confused57 on 2006-08-12
Here's a guide for uninstalling Ubuntu:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

You "may" need to reinstall Ubuntu first, I'm not sure, at least the link may give you some ideas.

---

### Post by orb9220 on 2006-08-12
Yes if you have boot from cd as your fist boot device in bios then your cd should boot regardless of what is on the hd mbr.

---

### Post by Hyuuga on 2006-08-12
Yes i bloody well put the boot options

> i've tried specifying it to boot from CD-rom with no luck

I've taken a look at the cd. I found out it was some crap that was "without boot". I'll see if i can get a hold of a cd that actually has boots :p

edit: nevermind, i cantacted the laptop supplier guys and they're sending a system restore disc (and of course apologising that such an essential didn't come with the laptop)

---

