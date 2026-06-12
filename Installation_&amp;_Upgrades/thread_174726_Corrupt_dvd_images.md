---
title: "Corrupt dvd images?"
date: 2006-05-12
forum: Installation &amp; Upgrades
---

### Post by pem on 2006-05-12
I downloaded ubuntu-5.10-dvd-i386.iso from two different sites (from the Ubuntu download page), one in Sweden and one in Ireland.

Both seems to be broken. The size is about 2.0GB (instead of the claimed 2.8GB in the file listing), and the MD5 checksum is wrong, despite that the download process seemingly finished without any problems.

Before I got around to check the MD5 sum, I tried to install it (under vmware), which didn't work. It got as far as to installing the base packages when it started to complain that it failed to retrieve things or that packages were corrupt, and after awhile it just gave up.

I then tried a CD image instead (ubuntu-5.10-install-i386.iso), which worked fine.

---

### Post by NoUse on 2006-05-12
Is it possible for you to download the image using bittorrent?  Bittorrent will make sure the image is downloading properly before finishing.

---

### Post by pem on 2006-05-12
[QUOTE=NoUse]Is it possible for you to download the image using bittorrent?  Bittorrent will make sure the image is downloading properly before finishing.[/QUOTE]

No, bittorrent is not an option.

A normal download should work anyway - firefox will tell if it got interrupted.
Note that the final size of the file is the one that firefox says it's going to download from the start.

---

### Post by NoUse on 2006-05-12
try using wget to download the image.  If you run wget -c [http://path/to/iso.iso](http://path/to/iso.iso) and have the 2GB you already downloaded in your current directory, wget will pick up where that file left off.

---

### Post by pem on 2006-05-15
[QUOTE=NoUse]try using wget to download the image.  If you run wget -c [http://path/to/iso.iso](http://path/to/iso.iso) and have the 2GB you already downloaded in your current directory, wget will pick up where that file left off.[/QUOTE]

Thanks, this seems to work. I get the right size and correct md5 sum now.
(I downloaded from scratch with wget.)

This is worrying however, that Firefox happily says it will dowload 2GB and then
does this, without any hint that it's actually not the complete file...

---

