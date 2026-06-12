---
title: "[SOLVED] Uninstall OpenGEU"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by zoso375 on 2008-01-24
...or geubuntu, whatever you wanna call it.  I already had a dual-boot (XP and Ubuntu), and decided to give OpenGEU a try.  I was fairly impressed with the live CD, so I installed it (yep, now 3 OSs on my PC), and of course it just cut the already existing ext3 system in half and installed itself in /sda.  But, after toying with it some more, I'm not very impressed.  I like my good ol' GG too much (or maybe I'm just too lazy to do all that customizing again).  Anyway, I want to uninstall and basically just undo the changes I made, and give that hard drive space back to Gutsy.  I'm not extremely experienced at partitioning, so I was hoping to get some help...it's not something I like to mess with, given that the possible mistakes outweigh the learning curve.  Any ideas on the best way to do this?  Thanks in advance...

---

### Post by Partyboi2 on 2008-01-25
You should be able to boot from the ubuntu live cd and use partition editor (System>Admin>Partition editor) and delete that partition then add the free space to xp or ubuntu with the resizing tool that is part of partition editor.
Just make sure you know what partition geubuntu is on before deleting it.

---

