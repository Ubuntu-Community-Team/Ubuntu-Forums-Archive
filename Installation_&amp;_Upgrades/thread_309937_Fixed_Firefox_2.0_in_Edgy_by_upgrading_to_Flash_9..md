---
title: "Fixed Firefox 2.0 in Edgy by upgrading to Flash 9.0"
date: 2006-11-30
forum: Installation &amp; Upgrades
---

### Post by fragmental on 2006-11-30
After upgrading to Edgy, Firefox would randomly crash. Flash seemed like a likely culprit so I upgraded to flash 9.0 and it stopped.  It may be possible to also fix it by simply reinstalling flash 7.0.  I'm not sure, I haven't tried that.  Flash 9.0 hasn't given me any problems so far, but it is prerelease software.

I'm fairly certain this has been discussed previously, but I wanted to share my experience anyway.

---

### Post by gborzi on 2006-11-30
I have had firefox crashes linked to flash, e.g. when opening youtube. I fixed these problems (still using flash 7.0) by adding the following line > export XLIB_SKIP_ARGB_VISUALS=1 to /etc/firefox/firefoxrc .

---

