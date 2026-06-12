---
title: "GPG errors since upgrade from 11.04"
date: 2011-10-28
forum: Installation &amp; Upgrades
---

### Post by fallenshadow on 2011-10-28
> W:GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192
 
Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>, W:GPG error: [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 

Anyone have a fix for the above errors? Ive looked at solutions all over the internet but nothing solves it for me.

I get these messages everytime I run update manager and its quite annoying! I should mention that I have this problem on my desktop PC as well as this netbook im currently using.

---

### Post by dino99 on 2011-10-28
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5 
(if this key is the good one)

[http://www.ubuntugeek.com/fix-for-gpg-error-httpextras-ubuntu-com-maverick-release.html](http://www.ubuntugeek.com/fix-for-gpg-error-httpextras-ubuntu-com-maverick-release.html)

---

### Post by fallenshadow on 2011-10-28
Tried that already... guess I can try it again. :/

---

### Post by fallenshadow on 2011-11-01
This problem seems to have sorted itself somehow. :confused:

Im confused but happy! :D

---

