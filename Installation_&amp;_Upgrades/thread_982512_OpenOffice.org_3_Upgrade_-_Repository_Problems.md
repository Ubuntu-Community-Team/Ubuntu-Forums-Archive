---
title: "OpenOffice.org 3 Upgrade - Repository Problems"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by iaskedalice09 on 2008-11-14
I'm using [this guide](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml) that adds an OOorg repository and gets 3.0 from that, rather than replace it in the Ubuntu synaptic.

My problem is with the repos itself. From the error messages, I gather it gets some, but others are not there.

```

W: Failed to fetch http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/Review/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/image/binary-i386/Packages.gz  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Is it a broken or bad repos? Many have used this success have so I think it's either a 404 or just server overload. If I am right, what are alternative repos I can use?

If I'm wrong, what's a fix?

Feedback is greatly appreciated.

THANK YOU!
bobby

---

### Post by inobe on 2008-11-14
many have installed it with the use of this site

[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

if your using x64 bit' you can snatch the tar here
[ftp://ftp.ussg.iu.edu/pub/openoffice/stab...n-US_deb.tar.gz](ftp://ftp.ussg.iu.edu/pub/openoffice/stab...n-US_deb.tar.gz)

many did not opt to uninstall openoffice 2 !

---

### Post by drs305 on 2008-12-31
Here is the repository line I use, which just worked fine:
```

deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main 

```

You could also add " universe multiverse restricted " if you want but they appear empty at the moment, at least for 64-bit intrepid.

If you aren't sure how to edit sources.list to delete a bad entry and add another just let us know and post the contents of /etc/apt/sources.list

---

