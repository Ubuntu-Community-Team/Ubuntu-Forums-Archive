---
title: "xsane &quot;no device available&quot;"
date: 2006-10-22
forum: Installation &amp; Upgrades
---

### Post by jynyl on 2006-10-22
Fresh install, with HP psc Photosmart 2510 printer scanner connected over local LAN.  Running Kubuntu 6.06, and can print to this printer ok.
When running xsane, it comes up with error "no devices available".
How do I get this working?

This scanner works fine from another box running Mandriva 2006 with xsane 0.97.

TIA

Peter

---

### Post by jynyl on 2006-10-24
Seems to be working now.

I installed sane-utils and xinetd, then used
 ```
hp-makeuri 192.168.1.106
```
which makes a URI for sane like this
 SANE URI: hpaio:/net/psc_2500_series?ip=192.168.1.106

Then xsane worked from command line with
 ```
xsane: "hpaio:/net/psc_2500_series?ip=192.168.1.106"
```

kmenuedit didn't seem to save any changes to the menu item (to change the 
xsane command as above) even when run with sudo, but manually editing the 
exec= line in this file
 /usr/share/applications/xsane.desktop
seems to do the trick.

HTH

Peter

---

