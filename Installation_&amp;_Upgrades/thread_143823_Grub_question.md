---
title: "Grub question"
date: 2006-03-13
forum: Installation &amp; Upgrades
---

### Post by lensisson on 2006-03-13
I think I originally put this in the wrong forum so I'm re-posting here.
I'm about to install Ubuntu over another Linux on a machine that dual-boots with Win XP. The current version of Grub is 0.95. Will the Ubuntu install update Grub and retain the dual-boot Grub config? Also, is there a good tutorial on how Grub works and how to change its config, etc.? Thanks.

---

### Post by Xian on 2006-03-13
[QUOTE=lensisson]Will the Ubuntu install update Grub and retain the dual-boot Grub config? Also, is there a good tutorial on how Grub works and how to change its config, etc.? Thanks.[/QUOTE]

Yes, when you install Ubuntu it will go about the process as a new event, and when you get to the grub module just be sure to place it in the MBR and you will maintain your dual-boot status. There are a lot of tutorials on the web available via google and in the Ubuntu wiki.

---

### Post by lensisson on 2006-03-13
Thanks Xian! Do you know if there is a way to find out whether GRUB is in my mbr now or in a boot partition? It is working great now--so I'd like to leave well enough alone. Grub got installed by Mandrake and I don't remember if I was given an option. It seems that I've heard you should avoid putting Grub in the MBR because of XP and/or Windows antivirus software???

---

### Post by dermotti on 2006-03-13
I have grub on my windows xp mbr, no problems.

---

