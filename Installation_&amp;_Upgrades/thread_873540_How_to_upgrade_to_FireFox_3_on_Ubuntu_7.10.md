---
title: "How to upgrade to FireFox 3 on Ubuntu 7.10?"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by HuBaghdadi on 2008-07-29
Hi.
I'm using Ubuntu 7.10.
How to upgrade FireFox 2.0.16 to FireFox 3?
Please, I don't want to loose my current profile, bookmarks, themes, addons ...
Thanks.

---

### Post by forger on 2008-07-29
I think the package in backports will use your 2.0 profile:
[http://packages.ubuntu.com/gutsy-backports/firefox-3.0](http://packages.ubuntu.com/gutsy-backports/firefox-3.0)

Click on your Ubuntu architecture to install it:
64-bit:
[http://packages.ubuntu.com/gutsy-backports/amd64/firefox-3.0/download](http://packages.ubuntu.com/gutsy-backports/amd64/firefox-3.0/download)
32-bit:
[http://packages.ubuntu.com/gutsy-backports/i386/firefox-3.0/download](http://packages.ubuntu.com/gutsy-backports/i386/firefox-3.0/download)
PowerPC:
[http://packages.ubuntu.com/gutsy-backports/powerpc/firefox-3.0/download](http://packages.ubuntu.com/gutsy-backports/powerpc/firefox-3.0/download)

---

### Post by HuBaghdadi on 2008-07-29
Please correct me if I'm wrong but it seems to that this package is FireFox 3 beta 4 ?

---

### Post by forger on 2008-07-29
hm.. right, outdated backports, someone should check that out :)

You might want to try ubuntuzilla:
[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

---

### Post by RuleMaker on 2008-07-29
To update your firefox you must start it as root:
```
gksudo firefox
```(in terminal)
And then from "Help" menu (in firefox) choose check for updates.

---

### Post by HuBaghdadi on 2008-07-29
I tried it but "check for updates" item isn't enabled.

---

### Post by RuleMaker on 2008-07-29
Sure it isn't because you haven't done as I told you.
You must start firefox as root and then the "Check for updates" will be enabled.
To start firefox as root type in terminal:
```
gksudo firefox
```

---

### Post by forger on 2008-07-29
Hint: first exit your current firefox, menu File > Exit (or Quit) :)

---

### Post by canadiandude007 on 2008-07-29
If you want to test out Firefox 3 and keep Firefox 2.0.0.x then you can also go to the Mozilla site and download Firefox to install locally and run it locally while you maintain Firefox 2.0.0.x as your main link.

Go to the Firefox download site to get the compressed file:
[http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html)

After downloading the file, decompress it and try it out.

Hope that helps!

---

### Post by HuBaghdadi on 2008-07-29
Same thing, the item is disabled...

---

### Post by HuBaghdadi on 2008-07-29
No, I want to make FF3 the default browser instead of FF2.

---

### Post by forger on 2008-07-29
Ok, so what about ubuntuzilla then?

---

### Post by SkonesMickLoud on 2008-07-29
Try:

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by aysiu on 2008-07-29
> **SkonesMickLoud said:**
> Try:

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)
I'd also recommend this method you've linked to (since I wrote it).

Ubuntuzilla is a script that automates the process and does a few other things (checks for localization, checks the integrity of the download, etc.), but it's a little more involved.

The *gksudo firefox* and *Check for Updates* method will not work. I don't know why someone kept suggesting it. First of all, the *Check for Updates* will install updates only within a version (so newer versions of Firefox 2 if you have 2 installed or newer versions of Firefox 3 if you have 3 installed). It will not upgrade you from 2 to 3. Also, it will not work at all if you're using the Ubuntu version of Firefox. It will work on only the Mozilla version of Firefox.

---

