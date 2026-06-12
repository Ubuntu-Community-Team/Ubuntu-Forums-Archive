---
title: "home directories location"
date: 2011-04-24
forum: Installation &amp; Upgrades
---

### Post by HunkirDowne on 2011-04-24
I have wubi installed (as Kubuntu 10.04) in Windows 7 on an NTFS host partition.  Although my wubi installation should be temporary it has persisted for some time but I keep going back and forth with my documents and it is causing me some pain when wubi locks up.

I intend for wubi to be temporary but still last a little while longer.  Can I just create symbolic links for my main home subdirectories?

These I would like to link to /host/Users/<user>/<subject>:
> ./Downloads
./Public
./Pictures
./Documents
./Videos
./Music
./Templates


IOW:
```
cd ~/Documents
find . -depth -type f -print0 | cpio --null -pvd /host/Users/hunkirdowne/Documents
cd
rm -rf ~/Documents
ln -s /host/Users/hunkirdowne/Documents ~/Documents
```
and repeat for all the subjected subdirectories.

Of course ~/Desktop and all the ~/.directories and ~/.files would remain (as well as ~/bin/firefox), but anyone see a problem with that (other than that blamed executable bit on all NTFS and FAT text files; bother)?

---

