---
title: "beryl issues"
date: 2007-03-09
forum: Installation &amp; Upgrades
---

### Post by aliyanage on 2007-03-09
Hi all,

I went on to the bery-project.org site and installed everything creating the script just how it is written down there. Here is the link

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia)

When starting beryl by typing beryl or beryl-manager it will somehow start but nothing really changes except for the fact that I don't have any window frames when opening up a new window and when opening a terminal it's just blank meaning white.
I ran the script again since I saw that I used the wrong deb's, but still no good.

Here is what I run on:
Acer Aspire 9410
Nvidia GeForce go 7000

could some please help me get this running or undo the script that I just ran?

thanks a lot in advance
Andrew

---

### Post by aliyanage on 2007-03-09
okay guys, this issue has been solved.

I tried installing it again and found out that basically I had to set the depth in the xorg.conf file to 24 instead of the 16 which it was before....

damn it feels good to solve it on your own :-D :guitar:

---

