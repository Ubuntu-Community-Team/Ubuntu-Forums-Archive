---
title: "Flash 9 Workaround"
date: 2006-09-15
forum: Installation &amp; Upgrades
---

### Post by donniep152 on 2006-09-15
Don't know if this has been posted, but it works for me until such time as Adobe gets to linux.

We need to install wine, wine cabextract and ies4Linux.  I know purists might balk, but if you need flash9 capabilities, this will work.

from terminal:  

sudo apt-get install wine
sudo apt-get install wine cabextract

then go here:  [http://www.tatanka.com.br/ies4linux/index-en.html](http://www.tatanka.com.br/ies4linux/index-en.html) and download the ies4Linux package to your desktop.  extract it and run ies4Linux setup.  this will install Internet Explorer for Linux under wine and also Flash9.

If you're using Firefox, you can the install the extension IEView or IEView Lite which will allow you to right click on a flash link and open just that link in IE.  You will need to change the default path in IEView to your current IE installation.

Hope this helps.

---

### Post by x64Jimbo on 2006-09-15
How about wine + windows firefox? I've been using this method for quite a while with no issues.

---

### Post by replicant on 2006-09-15
any particular method used to successfully install windows firefox and the flash plugin? i'm assuming it can't be near as hard as it was to get world of warcraft finally working.

thanks!

---

### Post by donniep152 on 2006-09-16
Once I had wine installed, all I did was download the windoze version to my desktop and double click on the .exe installer and wine handled the rest including a start icon on my desktop.  I have to say wine has come a long way since it's inception.

---

