---
title: "Installing 8.04 over 7.10"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by rpg on 2008-05-09
I have Windows and U7.10 running on a laptop.  I want to install 
U8.04 in the U7.10 partition.  I cannot do an upgrade, because I
don't have wireless working on this machine yet.  If I run 
U8.04-Live, and ask to install, it wants to keep 7.10, and 
install 8.04 in the same partition.  I'm a little afraid of a
manual partition, because I don't want to accidentally wipe out
Windows.  

Any suggestions?  Thanks!!

---

### Post by logos34 on 2008-05-09
One option is to get the 8.04 Alternate iso -- you can upgrade directly from that.

If you overwrite 7.10 root, make sure to backup your documents because it erases the whole partition

[https://help.ubuntu.com/community/HardyUpgrades?highlight=%28upgrade%29#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d](https://help.ubuntu.com/community/HardyUpgrades?highlight=%28upgrade%29#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d)

---

### Post by Pumalite on 2008-05-09
You can install Hardy on top of Gutsy. Go Manual and pick the old partitions (ext3)(xp is ntfs). Ignore /swap. The installer will do the rest. You'll have a new Grub and still dual boot.

---

### Post by rpg on 2008-05-09
When I go to "manual partition", it appears that it will be placing
8.04 in the 7.10 partition; but this isn't clear.  It also asks if
I want to "import" Windows, and I'm not sure what that means. . .

---

### Post by ripin1 on 2008-05-09
i acedently killed my windows partion. now all i have is hardy. its working pretty well but i am only 11 so i have trouble doing anything that involves editing my kernal or something like that.

---

### Post by Pumalite on 2008-05-09
Don't import anything. Do you want to install Hardy on top of Gutsy or side by side?

---

### Post by rpg on 2008-05-09
suppose I use Gparted, and simply delete the partition containing
7.10, giving the whole disk to Windows.  Then, I would install 8.04
on the "unused space".  Would that work?

---

### Post by rpg on 2008-05-09
I want to install Hardy on top of Gutsy, wiping out Gutsy.

---

### Post by Pumalite on 2008-05-09
It would work but much riskier. Manual gives you total control. It's your choice.

---

