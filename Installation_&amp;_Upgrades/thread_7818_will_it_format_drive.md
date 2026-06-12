---
title: "will it format drive?"
date: 2004-12-11
forum: Installation &amp; Upgrades
---

### Post by maurik on 2004-12-11
I've decided to install linux - ubuntu , I wanna run an XP / Linux dual boot. 

At the mo im having some queries. I have a 80gb harddrive. I have partioned it c:\  = 30 gb &  d:\ = 50 gb  I have XP Pro installed on the d:\ drive. At first i thought there'd be little problems.

However just recently while testing a file explorer program i made in vb6 i notced that the c:\ drive contains certain "valuable" files which are not visible in windows explorer unless i have "do not show system files" off...

I'm worried that if i install linux on my c:\ drive it will be formatted and XP will not be able to start up as it needs those files...

here's which files they are: [IMG]http://img27.exs.cx/img27/1156/files0gz.jpg[/IMG] 

What should i do?!
P.S. is ubuntu a-ok with ntfs?!

---

### Post by Rancoras on 2004-12-11
Don't install Ubuntu to your C: drive.  It **will** be formatted.  You would want to delete your D: drive and use the free space to partition for your Ubuntu install.  There will be a point during the install where it should detect your windows install and modify grub for dual booting.  As always, make sure you have a good backup of anything you don't want to lose from your windows install.

---

