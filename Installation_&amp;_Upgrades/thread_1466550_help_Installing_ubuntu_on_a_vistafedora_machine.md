---
title: "help Installing ubuntu on a vista/fedora machine"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by maldonw on 2010-04-30
hello all
first let me start off that I am very new at this (like days new)

I have a vista/fedora laptop and I decided I wanted to load ubuntu as well.I started a fresh install of ubuntu in an  newly created partition. This  created a bit of a  problem. grub  now sees all 3 OS's however  when i try to boot fedora I get the  following error : [COLOR=Red]you must load kernel first[/COLOR] [COLOR=Black]it  then kicks me back to the grub page to choose another  OS[/COLOR].  I  loaded ubuntu and did a sudo blkid and got this 

[COLOR=Red]wilfredo@wilfredo-laptop:~$ sudo blkid
[sudo] password for wilfredo: 
/dev/sda1: UUID="20378F114179A3DD" TYPE="ntfs" 
/dev/sda2: UUID="b8ebdef5-19a0-4a0e-b37c-d87928281842" TYPE="ext4" 
/dev/sda3: LABEL="Fedora-12-i686-L"   UUID="c89d7967-25aa-44e0-8ecd-6d21e57d6797" TYPE="ext4" 
/dev/sda5: UUID="a91f19e1-b82c-4a9e-b49b-9cced833c1cf" TYPE="ext4" 
/dev/sda6: UUID="1db22484-abdd-440c-912b-b859ef12ea87" TYPE="swap" 
wilfredo@wilfredo-laptop:~$ 
[/COLOR]
any ideas??

---

### Post by maldonw on 2010-04-30
bump

---

### Post by maldonw on 2010-04-30
just some other stuff i tried. I did a grub update as well and that didnt work.

---

### Post by oldfred on 2010-04-30
When you installed Fedora did you install its boot loader to the MBR, the boot partition - PBR, or not install it?

To document where everything is at:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

Some older related posts:
See Kansasnoob comments 40 & 42 Install grub 1.98 (lucid std) & to fix major grub issues
here was a BIOS option setting in the boot loader device selection in the Fedora installer. Comment #44
[http://ubuntuforums.org/showthread.php?t=1415879](http://ubuntuforums.org/showthread.php?t=1415879)
[http://ubuntuforums.org/showthread.php?t=1388777](http://ubuntuforums.org/showthread.php?t=1388777)
[http://ubuntuforums.org/showthread.php?t=1367305](http://ubuntuforums.org/showthread.php?t=1367305)

---

