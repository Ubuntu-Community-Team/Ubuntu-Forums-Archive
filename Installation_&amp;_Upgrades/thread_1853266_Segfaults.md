---
title: "Segfaults"
date: 2011-10-01
forum: Installation &amp; Upgrades
---

### Post by Dragon12 on 2011-10-01
Greetings,

I've just switched from Kubuntu 8 to 11 and I've managed to do updates until recently. I get a notification that there are updates available using KPackageKit. When I try to update, I get a dialog box that says its reading a list and then the dialog box disappears. I never see a list of available updates on KPackageKit. Fearing that maybe a bug cropped up in a previous update I tried the CL and get pretty much the same thing.

I checked dmesg and I get the following error;

```
 [ 4859.598270] packagekitd[2252]: segfault at c1538500 ip 00ece5af sp b6ff9f10 error 5 in libapt-pkg.so.4.10.1[e89000+10b000]
[ 4872.189633] packagekitd[2265]: segfault at c1613500 ip 00e115af sp b70d4ef0 error 5 in libapt-pkg.so.4.10.1[dcc000+10b000]
[ 4873.584536] packagekitd[2275]: segfault at c1473500 ip 071c85af sp b6f34f10 error 5 in libapt-pkg.so.4.10.1[7183000+10b000]
[ 4885.443954] packagekitd[2285]: segfault at c14bf500 ip 00c0b5af sp b6f80ef0 error 5 in libapt-pkg.so.4.10.1[bc6000+10b000]
[ 4886.844410] packagekitd[2295]: segfault at c15dd500 ip 00c975af sp b709ef10 error 5 in libapt-pkg.so.4.10.1[c52000+10b000]
[ 5113.803964] packagekitd[2340]: segfault at c15b7500 ip 010215af sp b7078f10 error 5 in libapt-pkg.so.4.10.1[fdc000+10b000]
[ 5614.834586] apt-get[2467]: segfault at c2434500 ip 001a25af sp bfbece90 error 5 in libapt-pkg.so.4.10.1[15d000+10b000]
[ 6729.792319] apt-get[2556]: segfault at c24d0500 ip 00b265af sp bff0baa0 error 5 in libapt-pkg.so.4.10.1[ae1000+10b000]
[ 7006.631801] apt-get[2575]: segfault at c2499500 ip 007075af sp bfacb3b0 error 5 in libapt-pkg.so.4.10.1[6c2000+10b000]
[ 7229.977155] apt-get[2585]: segfault at c2447500 ip 0046e5af sp bf9647b0 error 5 in libapt-pkg.so.4.10.1[429000+10b000]

```


I know that segfaults usually have something to do with bad RAM. So I swapped out the RAM with some known good sticks but I'm finding the same problems still occur. 

Does anyone have any suggestions? Answers? Ideas?

Thanks in advance! :guitar:

---

### Post by 2F4U on 2011-10-02
You should first try

```
sudo apt-get clean
``` 

or

```
sudo apt-get autoclean
```

After that, try to update using apt-get.

If this doesn't help, try to remove **/var/cache/apt/pkgcache.bin** and **/var/cache/apt/srcpkgcache.bin.**

---

### Post by Dragon12 on 2011-10-04
Thanks 2F4U,

That worked. Even KPackageKit works now. Must have been too much crap built up.

---

