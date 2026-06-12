---
title: "Can not match ANY xubuntu 16.04 download with md5sums"
date: 2017-06-09
forum: Installation &amp; Upgrades
---

### Post by Seadevil on 2017-06-09
i downloaded this program 5 times already and  MD5SUM cannot match the numbers.

this is 64bit download.

seems there is only ONE site to download from. Torrents DO NOT work. is there someway to

download direct?

---

### Post by deadflowr on 2017-06-09
Did you try from here:
[http://cdimage.ubuntu.com/xubuntu/releases/16.04/release/]("http://cdimage.ubuntu.com/xubuntu/releases/16.04/release/")

---

### Post by Seadevil on 2017-06-09
ooops....yeah, I went here and downloaded direct the very first time.  but that didn't match either.
guess i'll try the i386 version.
thanks for responding.

---

### Post by Impavidus on 2017-06-09
> **deadflowr said:**
> Did you try from here:
[http://cdimage.ubuntu.com/xubuntu/releases/16.04/release/](http://cdimage.ubuntu.com/xubuntu/releases/16.04/release/)

And I assume you also compared with the list of md5sums from that same site, right? I just checked and my old xubuntu-16.04-desktop-amd64.iso I still have on disk matches:```
$ md5sum xubuntu-16.04-desktop-amd64.iso
368896fb3643d543b7e7757f1aaba932  xubuntu-16.04-desktop-amd64.iso
```
For some reason I doubt that downloading a different image gives you a higher probability of a matching md5sum. For the first 5 download attempts, did you get 5 different non-matching md5sums? In that case your internet connection is really flaky, but repeated attempts (5, 50, 50000 attempts, I can't say) may eventually lead to a match. But you may have to consider other download possibilities. If you got 5 times the same non-matching md5sum, there's something wrong with the way you check the md5sum.

---

