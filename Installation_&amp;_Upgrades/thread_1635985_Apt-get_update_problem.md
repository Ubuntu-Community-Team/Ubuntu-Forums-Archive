---
title: "Apt-get update problem??"
date: 2010-12-02
forum: Installation &amp; Upgrades
---

### Post by nomko on 2010-12-02
Hi,

I've got an apt-get problem:
> [I]Apt authenticationproblem

Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check".[/I]

When i click on check the following message apears:

> W: An error occurred while verifying the signatures. The repository is not updated and the previous index files will be used. GPG error: [http://linux.dropbox.com](http://linux.dropbox.com) hardy Release: The following signatures were invalid: 1 NODATA NODATA 2

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/lucid/Release](http://linux.dropbox.com/ubuntu/dists/lucid/Release)

W: Collect Some index files failed, they have been ignored, or old ones used instead.


What does this mean?? And what the cause of this problem and does anyone know a solutions??
Many thanks!

---

### Post by philinux on 2010-12-02
Need to see your sources list. The error mentions Hardy and lucid.

Open a terminal.

```
cat /etc/apt/sources.list
```

Paste the output back here. Don't forget to wrap code tags around it.

---

### Post by nomko on 2010-12-02
My sourcelist:
> 
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid main restricted
 
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
 
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid universe
 
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid-updates universe
 
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid multiverse
 
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
 
deb [http://www.ftd4linux.nl/releases/ubuntu](http://www.ftd4linux.nl/releases/ubuntu) lucid main
deb [http://mirrors.dotsrc.org/getdeb/ubuntu](http://mirrors.dotsrc.org/getdeb/ubuntu) lucid-getdeb apps
deb [http://mirrors.dotsrc.org/getdeb/ubuntu](http://mirrors.dotsrc.org/getdeb/ubuntu) lucid-getdeb games
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid non-free
deb [http://ppa.launchpad.net/vala-team/ppa/ubuntu](http://ppa.launchpad.net/vala-team/ppa/ubuntu) lucid mainI do need to tell you that this is not the complete list. Under /etc/apt/sources.list.d there are some more source listings and one of them is for Dropbox:
 
> deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) lucid main
 
[http://img716.imageshack.us/img716/546/softwarebronnen02122010.png](http://img716.imageshack.us/img716/546/softwarebronnen02122010.png)

---

### Post by nomko on 2010-12-03
Nobody?

---

### Post by sikander3786 on 2010-12-03
GPG key for dropbox is missing. You can try adding that as mentioned here.

[http://forums.dropbox.com/topic.php?id=10123](http://forums.dropbox.com/topic.php?id=10123)

Or see this.

[http://forums.dropbox.com/topic.php?id=20075](http://forums.dropbox.com/topic.php?id=20075)

Or this.

[http://www.webupd8.org/2009/10/dropbox-repository-finally-available.html](http://www.webupd8.org/2009/10/dropbox-repository-finally-available.html)

---

### Post by nomko on 2010-12-03
> **sikander3786 said:**
> GPG key for dropbox is missing. You can try adding that as mentioned here.
 
[http://forums.dropbox.com/topic.php?id=10123](http://forums.dropbox.com/topic.php?id=10123)
 
Or see this.
 
[http://forums.dropbox.com/topic.php?id=20075](http://forums.dropbox.com/topic.php?id=20075)
 
Or this.
 
[http://www.webupd8.org/2009/10/dropbox-repository-finally-available.html](http://www.webupd8.org/2009/10/dropbox-repository-finally-available.html)
 
 
Why is it missing? The website of Dropbox gives u 2 options: either by hand or by a .deb file. I've done both but still getting the same error. It's like that the GPG key is not correctly added using both options. And'i'm using 10.04 Lucid Lynx, i hope that solution for Karmic will help. Thanks anyway!

---

