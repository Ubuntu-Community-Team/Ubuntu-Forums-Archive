---
title: "MBR Apocalypse!"
date: 2008-09-02
forum: Installation &amp; Upgrades
---

### Post by Lachinchon on 2008-09-02
The background: HD#1 has Vista and a recovery partition; hd#2 is a data disk. I added hd#3 to be exclusively Ubuntu. Fearful of something messing up my data drive, I physically removed it before installing Ubuntu on hd#3. All went well. I then reinserted my data drive and the world came close to ending. Grub refused to load, citing numerous errors, the last one being error 21 (which I believe is drive not found). I could not boot into anything except a black error screen. After much gnashing of teeth, I recovered the mbr on hd#1 using the fixmbr command in the vista console. Unfortunately, my other drives were unrecognized. I recovered hd#2 by resetting my cmos (removing the battery!). So now I am back to more or less normal - I can boot into Vista and my data drive works as normal. HD#3, containing Ubuntu, is only recognized in device manager.

  So, here is the question: I want to get Ubuntu back up on hd#3 without f%*king up my Vista install. I think my options are these:
1. reinstall Ubuntu using the install cd, but somehow keep Grub on hd#3, NOT on my Vista disk, then use EasyBCD to add Ubuntu to the Vista bootloader. Or,
2. reclaim hd#3 through Vista (I am not quite sure how, yet), then install Ubuntu onto essentially a Vista drive (reclaimed hd#3) using WUBI.

Please give me your thoughts and suggestions before I impale myself again.

Lachinchon.
There are some things it is impossible to know, but it is impossible to know these things.

---

### Post by bubba_169 on 2008-09-02
My guess: What happened was when you installed grub it was told to look on HD#2 for the ubuntu files, because you unplugged your other drive! This means when you plug in your other drive again the Ubuntu drive becomes HD#3 and grub is left looking for Ubuntu on your data drive.

If this is the case its a simple fix but a tricky solution. You need to install ubuntu (data drive unplugged), boot into ubuntu (data drive still unplugged) and change the ubuntu entry in /boot/grub/menu.lst to look at hd2 instead of hd1. Then shutdown, plug in your data drive and then boot ubuntu...

All this can be avoided by installing ubuntu with all drives plugged in :D

---

