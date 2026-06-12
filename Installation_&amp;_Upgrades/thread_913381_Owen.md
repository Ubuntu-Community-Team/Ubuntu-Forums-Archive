---
title: "Owen"
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by omb on 2008-09-07
Could anyone advise procedure for installation of Epson Stylus Photo Rx610 Printer/scanner to Ubuntu 8.4 please.

---

### Post by omb on 2008-09-07
???

---

### Post by ad_267 on 2008-09-07
Plug it in and go to System - Administration - Printing and click add new printer and follow the steps. To check the scanner is working you can open Applications - Graphics - Xsane Image Scanner.

You should also give your post a more descriptive title. Most people looking at "Owen" would ignore the post because they wouldn't think you're asking for help.

---

### Post by ad_267 on 2008-09-07
I had a look and it seems like Ubuntu has rx600, 620 and many other rx drivers but not 610. You might have to get the 610 drivers from this site: [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do) There are separate printer and scanner drivers.

Edit: It looks like that page uses .rpm packages rather than .deb so you might have to install them using alien from the terminal. See [http://www.ubuntugeek.com/install-rpm-files-in-ubuntu.html](http://www.ubuntugeek.com/install-rpm-files-in-ubuntu.html)

---

### Post by Sef on 2008-09-07
Please wait 24 hours before bumping you thread.  Thank you.

---

### Post by charonred on 2009-05-05
I setup my brothers rx610 and it wouldn't print in Intrepid.

When I tried the Jaunty live CD it printed, so I installed/upgraded to Jaunty (with printer connected and on).

Once upgrade was complete, I deleted previous rx610 printer, Jaunty then found a 'new printer' and presto it now prints in both Gnome and KDE, as well as XP in VirtualBox.

still having no scanner detection (new post)

---

### Post by blaisenamy on 2009-05-07
> **ad_267 said:**
> Plug it in and go to System - Administration - Printing and click add new printer and follow the steps. To check the scanner is working you can open Applications - Graphics - Xsane Image Scanner.

You should also give your post a more descriptive title. Most people looking at "Owen" would ignore the post because they wouldn't think you're asking for help.

Thanks, guys!  I was able to easily get my Stylus RX595 up and running due to this post!  However, I was hoping you could help me get the scanner portion working.  I went to Applications - Graphics - Xsane Image Scanner as you suggested, and it said there was no scanner.  Any suggestions?  You rock!

---

