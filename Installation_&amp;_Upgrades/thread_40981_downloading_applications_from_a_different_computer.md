---
title: "downloading applications from a different computer"
date: 2005-06-11
forum: Installation &amp; Upgrades
---

### Post by tipifire on 2005-06-11
downloading applications from a different computer.
How do you and/or the best way to download applications (like Wine or abiword) from a different computer and install the applications on mine (Ubuntu)? I do not have internet at home for my computer. And I directly do not see a way to download a application? I just installed Ubuntu for the first time. And as much as I like it, not many sites are offering the a direct download to burn to a CD? And what about updates? How does this work?

---

### Post by Alexander Kirillov on 2005-06-12
[QUOTE=tipifire]downloading applications from a different computer.
How do you and/or the best way to download applications (like Wine or abiword) from a different computer and install the applications on mine (Ubuntu)? I do not have internet at home for my computer. And I directly do not see a way to download a application? I just installed Ubuntu for the first time. And as much as I like it, not many sites are offering the a direct download to burn to a CD? And what about updates? How does this work?[/QUOTE]
 You can download apps, burn them to a CD, and then take to your computer. The problem is, you will have to hunt for dependencies manually: if you download wine, burn it on a CD, and try to install on your computer, then you may find that it requires another pacakge, so you will have to go back and download that, too. I do not know of an easy way around this. 


Try finding add-on CD. It contained a lot of software for Ubuntu and a script to install it. The CD author took it off-line for legal reasons (see [this thread](http://ubuntuforums.org/showthread.php?t=30147)), but you might still find copies through google. 

Failing this, go to [http://packages.ubuntu.com/hoary/](http://packages.ubuntu.com/hoary/) 

You can download the necessary packages from there, burn them to a CD, then install each of them using dpkg -i <packagefile>

---

