---
title: "Recently upgraded from 13.10 to 14.04 - system locking up"
date: 2014-05-21
forum: Installation &amp; Upgrades
---

### Post by jord1981 on 2014-05-21
Since this upgrade my system locks up somewhat randomly.  Two sure fire triggers: launch Firefox from the panel (it does not lock up if launched from the menu or desktop), or visit [http://beta.realtor.ca](http://beta.realtor.ca).  The freeze manifests it in 3 different ways: 1.) the screen turns distorted looking a bit like a mosaic of the colours the were on the screen at freeze; 2.) the screen freezes as is and I cannot move the mouse pointer; 3.) the screen goes black but the mouse pointer remains and can be moved.  In all cases, I cannot a shell with ctrl+alt+f1 and can only recover if I do a hard reboot.

My machine is a bit older, it is an Acer Aspire AST180.  Specs are here:[http://www.cnet.com/products/acer-aspire-t180-ua380a-athlon-64-3800-plus-2-4-ghz-1-gb-160-gb/specs/](http://www.cnet.com/products/acer-aspire-t180-ua380a-athlon-64-3800-plus-2-4-ghz-1-gb-160-gb/specs/)

Many thanks for any advice on how to resolve these problems.

---

### Post by jord1981 on 2014-06-03
I upgraded to 2GB of ram and this has not made any difference.

---

### Post by LastDino on 2014-06-03
Not exact but I'll pitch in some food for though.
I would usually first look into drivers when I get issues relating to things like ''screen being distorted''.
First, see if you get same issues when you try to boot into nomodeset. Hit F6 while grub getting loaded/booting and you should see the "linux" string at the bottom. Just go the the end and add "nomodeset".
If you don't then your problem is probably proprietary drivers? If you've them, disable them and if you don't, then install proprietary drivers by going into additional drivers in ''software & update'' manager. 

I would also recommend taking backup and doing fresh install as I rememeber me having firefox freez problem with 13.10, but not sure if this is root of your problem too. I have no issues with 14.04, by the way. And I've tried three different DE's (Unity, Xubu and Gnome). You might also consider sticking with Xubuntu side of the things considering your system is old.

---

