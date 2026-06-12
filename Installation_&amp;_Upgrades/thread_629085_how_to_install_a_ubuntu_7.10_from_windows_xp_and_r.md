---
title: "how to install a ubuntu 7.10 from windows xp and run a dual boot config. please help"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by bwjohnson88 on 2007-12-02
I've reviewed the other posts and none of them answer my question.  My issue is that I have windows xp on my computer now.  I downloaded wubi and am running that with ubuntu.  I want to know if there is a way to go from wubi to a full dual boot windows xp/ubuntu without reformatting the hard drive and trashing all of my important information.  I think i saw it somewhere on google a while ago but now i cant find it.  Please help if you know how.  

Once again, I want to install ubuntu as another operating system with windows xp already on my computer.  Any responses would be greaty appreciated.  THANKS!!! 

Oh and by the way, i am new to linux so i dont know a whole lot.:confused:

---

### Post by fmartinez on 2007-12-02
I'm not too familiar with wubi, but unless it offers an 'UPGRADE' option and is compatible with Ubuntu.. the only way would be to reformat your partition that has wubi on it. I'd recommend backing up your home directory prior to install / upgrade just in case.

---

### Post by curtis1552 on 2007-12-02
bugger on wubi, repartition the HDD. Don't reformat it.

The partition can be resized without data loss, when installing Ubuntu select the option to resize the partition (the 1st one). However, I will warn you that it still can corrupt the partition making it unusable. 

This means that you NEED TO BACKUP your important information BEFORE you try and install ubuntu.

When installing and prompted to overwrite the MBR select NO.
After the install it will still boot to windows.
Download and run a bootCD with Super GRUB.
This will overwrite the MBR and (almost) automaticaly.

---

