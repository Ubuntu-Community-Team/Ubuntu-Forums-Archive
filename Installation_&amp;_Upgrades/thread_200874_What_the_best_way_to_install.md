---
title: "What the best way to install?"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by inigmatus on 2006-06-20
Hi! I am still fairly new to Linux, probably know enough to kill a system, but not enough (I feel) to set one up right. I have the current setup:

1GB RAM 
1.8Ghz PIV

HD#1 100GB - NTFS XP Home Edition SP2
HD#2 20GB - empty
HD#3 45GB - FAT32

Video: ATI Radeon 9600 (RV350) 128MB

Obviously I want to dual boot to HD#2. I wanted to know what the best way to install Dapper on it would be. I have the following questions:

How should I partition HD#2? What sizes, what format, and in what order?

How can I ensure I get my ATI video card to work?

I have heard about the alternate CD versus the Desktop CD. Should I use the alternate CD, or am I just fine using the Desktop CD? 


I had Breezy on HD#2 before I wiped it clean (it was my first Linux install, over-customized to the hilt as I tried to make it look cool - heh but not as functional as I had hoped - and I didn't want to deal with the headache of bug and dependency hunting in a vain attempt to upgrade to Dapper as a noob). Suggestions?

---

### Post by aysiu on 2006-06-20
Here's a good place to start:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

### Post by inigmatus on 2006-06-20
[QUOTE=aysiu]Here's a good place to start:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)[/QUOTE]

Thanks for the link!

Since I have an ATI card, I heard that I should I use the alternate CD over the Desktop CD when installing Ubuntu? Is this true?

---

### Post by jpkotta on 2006-06-20
Your video card will almost surely work out of the box.  The hard part is getting hardware accelleration to work.  If you don't care about this, then you just have to install and forget it.  If you do care (you want to run OpenGL programs like games and Celestia, or you want to try Xgl), then look in the wiki ([https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)) or the forums.

---

### Post by inigmatus on 2006-06-20
[QUOTE=jpkotta]Your video card will almost surely work out of the box.  The hard part is getting hardware accelleration to work.  If you don't care about this, then you just have to install and forget it.  If you do care (you want to run OpenGL programs like games and Celestia, or you want to try Xgl), then look in the wiki ([https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)) or the forums.[/QUOTE]

Thanks for the quick response. You guys are totally awesome. This is why I love Ubuntu and this community so much.

---

### Post by inigmatus on 2006-06-20
[QUOTE=inigmatus]Thanks for the quick response. You guys are totally awesome. This is why I love Ubuntu and this community so much.[/QUOTE]

I also found this for installing ATI in safe graphics mode:
[http://www.ubuntuforums.org/showthread.php?t=191944&highlight=ati+safe+graphics](http://www.ubuntuforums.org/showthread.php?t=191944&highlight=ati+safe+graphics)

---

### Post by inigmatus on 2006-06-21
I'm all installed! I followed the ATI link I posted and I'm fully running Dapper and XP now. Thanks for the advice you all gave! This was the easiest install of Ubuntu yet for me.

---

