---
title: "Kernel Panic in Edgy after attempted Usplash theme installation"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by Rawrhunter on 2007-03-18
I finally decided to install ubuntu on my system yesterday, so I created a few new partitions. I kept a windows partition of 150gb, created a 100gb fat 32 partition (shared data between the 2 operating systems) and installed ubuntu (edgy) on the remaining 50gb. Everything was going generally well, I got all my drivers and software installed, and didnt come across anything I couldn't fix with a few minutes and some googling.

I got most of the important stuff out of the way, and decided to start looking at Gnome themes. I came across [http://www.gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468]("http://www.gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468") and decided to try it out.

I downloaded it and followed the instructions here: [https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765]("https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765")
Basically I seem to have killed my system. I restarted my computer and selected the default kernel and startup version (like I have a dozen times already) and was faced with the following error:
**Kernel panic - not syncing: VFS: Unable to mount root fs on unknown_block(0,0)**
Underneath is a blinking cursor but I am unable to type. Booting to windows works fine, and booting another kernel version gets a video driver incompatibility but allows me to login and use nano.

---

