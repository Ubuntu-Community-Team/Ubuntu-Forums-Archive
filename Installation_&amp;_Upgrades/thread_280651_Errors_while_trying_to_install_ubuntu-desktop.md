---
title: "Errors while trying to install ubuntu-desktop"
date: 2006-10-19
forum: Installation &amp; Upgrades
---

### Post by zergberg on 2006-10-19
When I try to install ubuntu-desktop, apt gives me this error:
```
Unpacking bittorrent (from .../bittorrent_3.4.2-6ubuntu2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/bittorrent_3.4.2-6ubuntu2_all.deb (--unpack):
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/Choker.py', which is also in package bittorrent-4.2.2.linux
Errors were encountered while processing:
 /var/cache/apt/archives/bittorrent_3.4.2-6ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

How do I fix this?

---

### Post by bswilson on 2006-10-19
What command did you run that generated this error?  Did you not just run this:

```
$ sudo apt-get install ubuntu-desktop
```

...or did you do something else?

---

### Post by randell6564 on 2006-10-19
> **zergberg said:**
> When I try to install ubuntu-desktop, apt gives me this error:
```
Unpacking bittorrent (from .../bittorrent_3.4.2-6ubuntu2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/bittorrent_3.4.2-6ubuntu2_all.deb (--unpack):
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/Choker.py', which is also in package bittorrent-4.2.2.linux
Errors were encountered while processing:
 /var/cache/apt/archives/bittorrent_3.4.2-6ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

How do I fix this?
This should not be preventing you from installing Dapper-Drake. It is only in reference to Bittorent.
Are you attempting to install Bittorrent so that you can download an Ubuntu  torrent file?
If so, then you are not actually installing the Upgrade this way, meaning that you did not do what 'bswilson' refered to,> sudo apt-get install ubuntu-desktop
So for now, forget about Bittorrent since what you are really after is Ubuntu 6.06!
Depending on your connection speed, why not just download the [Ubuntu 6.06 ]("http://ftp.ussg.iu.edu/linux/ubuntu-releases/6.06/")iso, burn it to a CD and install it that way?

---

