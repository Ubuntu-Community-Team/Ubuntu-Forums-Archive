---
title: "Partial upgrade problem."
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by varunbhatbm on 2008-04-03
Hi,
today my update manager showed available updates, I got a pop up saying partial updates are available.

I clicked partial upgrade then the following screen appeared. 
[ATTACH]64875[/ATTACH]

After some time.. I got a pop up 
[ATTACH]64874[/ATTACH]

Please tell me why the upgrade is failing, is this a normal s/w upgrade or its Ubuntu upgrade..?

---

### Post by zvacet on 2008-04-04
**system>admin>software sources>**uncheck all third party repos you added and try again.

---

### Post by kushykush on 2008-04-04
I have exactly the same problem.  My apprehension is that it has something to do with authentication of software sources.  I have tried to install the right keys but the authentication fails.  Instructions are incomplete as to how to download and authenticate.

However, the above is just a guess.

I need help here as much as the first writer.  I hope someone will care to respond.  It is important that the upgrade is fully completed and we do not see the "partial upgrade" errors again.

---

### Post by Brynster on 2008-04-04
I got around it by opening terminal and typing

 ```
sudo apt-get dist-upgrade
```

then entering my password when prompted. I didn't have any third party repos present on my vanilla install.

Hope this helps

---

### Post by kushykush on 2008-04-04
OK, I read another message down in this forum.  And it seems to suggest that it relates to certain updates in the kernel which are being deliberately held until the final release???  Here is the link:

[http://ubuntuforums.org/showpost.php?p=4640849&postcount=5](http://ubuntuforums.org/showpost.php?p=4640849&postcount=5)

If that is the case then there is nothing wrong.  What I have been doing is just closing the partial upgrade window.  Below it the window says, "your system is up to date."  Therefore, the above seems to be true i.e. that it is something which will go away when the final release is done in the next 20 days.

---

### Post by kushykush on 2008-04-04
I followed that command and got the following:
WARNING: The following packages cannot be authenticated!
  sysvinit-utils sysvinit initramfs-tools initscripts
Install these packages without verification [y/N]? 

I said y.  It updated.  I do not know if that will cause any problems.  But I was right it was an authentication problem.

---

### Post by kushykush on 2008-04-04
Again, there is a package (64-AMD) which cannot be updated.  I got the following in the end:

Selecting previously deselected package sysvinit-utils.
(Reading database ... 112838 files and directories currently installed.)
Unpacking sysvinit-utils (from .../sysvinit-utils_2.86.ds1-38_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/sysvinit-utils_2.86.ds1-38_amd64.deb (--unpack):
 trying to overwrite `/usr/bin/last', which is also in package sysvutils
Errors were encountered while processing:
 /var/cache/apt/archives/sysvinit-utils_2.86.ds1-38_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Partial upgrade remains.  I do not think this is a problem.

Just ignore the message and close the window.  This will be taken care of by the developers once they have tested and authenticated the package. And it seems to be related to the AMD-64 bit version not the 32 bit.

---

