---
title: "deleted  a non-ubuntu partition effeted grub"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by OOzypal on 2010-09-10
Hello

I have ubuntu in sda7. sda6 had bt4, sda3 had Win7. From Win7 I removed sda6. Now when I start my computer I get grub rescue. How can I tell grub that ubuntu in sda6 and not in sda7 anymore or how can I create sda6 again so ubuntu goes sda7.

Thx

---

### Post by oldfred on 2010-09-10
Grub also uses search and UUIDs so it should find boot partition. You can reinstall grub to the MBR. But to know where everything is at.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

