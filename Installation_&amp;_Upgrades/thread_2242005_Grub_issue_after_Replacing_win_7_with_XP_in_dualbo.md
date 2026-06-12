---
title: "Grub issue after Replacing win 7 with XP in dualboot setup"
date: 2014-08-29
forum: Installation &amp; Upgrades
---

### Post by jerrel2 on 2014-08-29
Hello friends,

I just started out with ubuntu, and could really use some help.

I have setup a dualboot by installing win 7 and afterwards unbuntu. All went and worked fine.

Later i decided that win xp would work better, so i made a backup in ubuntu of grub/mbr per instructions online, formatted my win 7 part and installed XP. XP took over the MBR as expected.

From the live USB i restored the grub.mbr also per instructions from the web, and wala GRUB started up again.

The issue is however, that the menu still diplays win 7, and when i select it, i get :

error:no such device: 4cd0XXXXXXXXX   
Setting partition to type 0X7  
press any key to continue

The system then boots in XP


My dual boot works, but my grub needs to be fixed.

Any advice on how to do this is appreciated.

Please see attached pic for error

---

### Post by jerrel2 on 2014-08-30
He Guys,

A simple boot-repair (recommended option) did the trick.

Tx

---

