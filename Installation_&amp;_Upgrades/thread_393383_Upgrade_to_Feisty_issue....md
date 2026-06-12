---
title: "Upgrade to Feisty issue..."
date: 2007-03-25
forum: Installation &amp; Upgrades
---

### Post by socomoddjob on 2007-03-25
Im trying to upgrade with the "update-manager -d".....

i get these errors during the install...


[B]Failed to fetch [http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)[/B]

Help.

---

### Post by socomoddjob on 2007-03-25
any ideas????

---

### Post by zvacet on 2007-03-26
```
sudo aptitude update
```
```
sudo aptitude upgrade
```

---

### Post by chaplan on 2007-03-26
i'm having the same problem. I triyed the comands you posted and the same error apears. What can i do????

---

### Post by soy Keymaster on 2007-03-30
I had this issue as well and the cause turned out to be duplicate entries in my /etc/apt/sources.list

To fix the problem:

1) open the "Software Sources" app under System > Administration
2) on the "Ubuntu Software" tab I unchecked then rechecked every item on the tab (Main, Universe, Restricted, Multiverse, Source Code) then clicked "Close"
3) clicked "Reload" when it came up
4) ran update-manager -d
5) enjoy feisty

---

### Post by koji on 2007-03-31
I've been experiencing this issues even for regular updates for some time.

After searching in the forums and testing all the suggested solutions it came out to be a proxy issue.

Deleted all duplicated sources.list entries and it was there again after two updates; changed servers to other country worked fine after first update and failed later; changed  sources.list to use ftp instead of http servers solved it.

It didn't make any sense after I realized that I am using oops to proxy all connections to internet except ftp.

I disabled apt use of proxy and ftp and http links in source.list worked fine again.

My suggestion:

1.- check for lines like:
Acquire::http::Proxy "http://127.0.0.1:8123";
in /etc/apt.conf (the IP address doesn't matter) and delete it (do a backup first!!)

This was enough for me. But other proxy configs that might affect are:

2.- HTTP_PROXY environment variables.

3.- Proxy definitions at the desktop level (KDE proxy configuration etc...)

I am pretty sure that point first is more that enough and 2 and 3 are superfluous because I believe that apt-get is not using these configs. If you are not in case 1, remember that you can be traversing 'transparent' proxies in your ISP. In this case changing your sources.list to use ftp links when available could be an acceptable solution.

regards

---

