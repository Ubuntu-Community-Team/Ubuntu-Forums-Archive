---
title: "Installing Ubuntu 7.10 on an already partitioned HDD"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by redserpent7 on 2008-05-03
Hi I have a problem... I have a windows xp already installed on my HDD on the default C:\ drive. My HDD has 4 partitions C,D,E and F each with an 20 GB capacity. I have tried to install Ubuntu on drive F: using manual partitioning, I have formated the drive to an  all compatible ext3 and tried to install Ubuntu. Everything went well until it started to install Grub. "Grub cannot be installed" error appeared.

I'm guessing it's because F: is not the boot drive and I have to install grub on C:. So how can I do that?? Or to be more clear, How can I install Ubuntu using the settings I mentioned??

---

### Post by Partyboi2 on 2008-05-03
Hi there, During installation setup on the last page there is a button call "Advanced" click on that and choose where to install grub  (hd0,0)

---

### Post by redserpent7 on 2008-05-04
Thanx, will try that. Is there any other things that I should know on installing Ubuntu with these HDD settings.

---

