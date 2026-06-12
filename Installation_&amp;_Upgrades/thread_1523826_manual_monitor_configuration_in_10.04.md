---
title: "manual monitor configuration in 10.04"
date: 2010-07-04
forum: Installation &amp; Upgrades
---

### Post by engine on 2010-07-04
So, despite the reasonable assertion that linux is a good way to get modern performance out of older hardware, 10.04 seems a bit picky about graphics chipsets. Thanks to various knowledgeable contributors, I think I've found out what to do ...

Still three questions, though:

[LIST]
[*]the release notes suggest disabling KMS by "booting with the 'nomodeset' option" &#8210; how do I do that?
[*]the release note also say that if disabling KMS is the answer, I can edit my grub config to make 'nomodeset' permanent. How do I find out whether I'm using grub 1 or grub 2?
[*]the 9.10 live CD recognised my Philips 190S monitor and set the resolution to 1280 * 1024 &#8210; an Internet-based installation of 10.04 did not recognise the monitor. Is this part of the same problem?
[/LIST]
Thanks in advance!

---

### Post by labinnsw on 2010-07-05
> **engine said:**
> the release notes suggest disabling KMS by "booting with the 'nomodeset' option" &#8210; how do I do that?

[http://ubuntuforums.org/showpost.php?p=9209655&postcount=5](http://ubuntuforums.org/showpost.php?p=9209655&postcount=5)

> **engine said:**
> the release note also say that if disabling KMS is the answer, I can edit my grub config to make 'nomodeset' permanent. How do I find out whether I'm using grub 1 or grub 2?
[http://ubuntuforums.org/showpost.php?p=9256793&postcount=17](http://ubuntuforums.org/showpost.php?p=9256793&postcount=17)

---

### Post by efflandt on 2010-07-06
You can try **nomodeset** boot parameter by hitting "e" at the grub menu and adding that parameter after **quiet splash** (or if that does not work, try deleting **quiet splash** and adding **nomodeset**, so you could see boot messages).

When you boot, if you see grub 1.98, that is the default grub2 used by 10.04.  You would not have grub1 (0.97) unless you did an upgraded from 9.04 or earlier at some point, instead of fresh install.  If you have the file /boot/grub/grub.cfg, you are using grub2.  But do not edit that, edit /etc/default/grub and use sudo with your editor (or gksu gedit) to make changes to that.

---

### Post by engine on 2010-07-17
Thanks for that! So far, I've replaced **quietsplash** with **nomodeset**, and that seems to have solved the problem. From your tip, I'll now cautiously try putting **quietsplash** back in to hide the boot messages &#8210; nothing there I understand anyway <g>

---

