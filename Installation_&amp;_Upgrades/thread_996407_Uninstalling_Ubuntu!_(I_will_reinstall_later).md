---
title: "Uninstalling Ubuntu! (I will reinstall later)"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by evilminininja on 2008-11-28
I need to uninstall ubuntu 8.10. I have dual-boot with vista but I realized i installed ubuntu in my vista partition, at least that is what I think i did. Now, how to i get rid of ubuntu without destroying vista (no installation vista disks since it came pre-installed on my laptop)

Reason I am doing this? I need more disk space on ubuntu so i can play WoW. I have been working at this for hours and would appreciate the help!

---

### Post by Partyboi2 on 2008-11-30
If you installed ubuntu using wubi then you should be able to uninstall ubuntu from add/remove. If you cannot uninstall it then you can do it the manual way, see [[COLOR=Blue]here[/COLOR]]("https://wiki.ubuntu.com/WubiGuide#Uninstallation"). If you installed ubuntu to its own partition then you you can boot a ubuntu live cd and use gparted (System>Admin>Partition Editor) and unmount your ubuntu partitions then delete them. Then use [[COLOR=Blue]super grub[/COLOR]]("http://supergrub.forjamari.linex.org/") disk to fix the mbr.

If you used wubi to install ubuntu on the windows partition then you can follow [[COLOR=Blue]this[/COLOR]]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?") to resize the virtual partition to make more space.
If you do have ubuntu on its own partition seperate from windows then you can use the ubuntu live cd and gparted to resize your partitions to make more room.

---

