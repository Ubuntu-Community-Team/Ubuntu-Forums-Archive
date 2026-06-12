---
title: "Wine &amp; Unreadable Font"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by rvickers on 2007-10-21
I've just done a scratch install of Gutsy and Wine. The winecfg has an unreadable font like it could be Hebrew maybe( just a guess ). I successfully loaded a windows app and it runs but some of the text is in this weird font. Any ideas???
Thanks

---

### Post by rvickers on 2007-10-21
Resolved with the following command:
 # cp /usr/share/fonts/truetype/freefont/*.ttf /home/roy/.wine/drive_c/windows/fonts

:guitar:

---

