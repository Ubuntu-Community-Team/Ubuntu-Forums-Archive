---
title: "Hardy upgrade problems"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by pcglue on 2008-05-16
I did an upgrade from Gutsy to Hardy, but there were errors during the upgrade.  Now, trying to use apt-get tells me to run "dpkg --configure -a".  When I do that, I get these errors:

```
Setting up docbook-xml (4.5-5) ...
update-xmlcatalog: cannot open catalog data /var/lib/xml-core/docbook-xml for writing: No such file or directory at /usr/sbin/update-xmlcatalog line 485.
dpkg: error processing docbook-xml (--configure):
 subprocess post-installation script returned error exit status 2
Setting up ttf-dejavu-core (2.23-1) ...
/etc/defoma/hints/ttf-dejavu-core.hints: Unable to open, or empty.
dpkg: error processing ttf-dejavu-core (--configure):
 subprocess post-installation script returned error exit status 1

```

and then a whole bunch of dependencies on these two packages that can't be installed/configured and then at the end...

```

dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
```

How can I fix the problems with the docbook-xml and ttf-dejavu-core packages?  Thanks for your help!

---

### Post by zenwalker on 2008-05-16
Well  before straight away upgrading to gutys, did u first update gutsy to the new gutsy packages in repo? Thats what the docs says right, if u have read it.

---

### Post by pcglue on 2008-05-16
> **zenwalker said:**
> Well  before straight away upgrading to gutys, did u first update gutsy to the new gutsy packages in repo? Thats what the docs says right, if u have read it.

Yes, I did.  I followed the upgrade instructions here:
[https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)
and had update-manager upgrade all the current gutsy packages first before upgrading from 7.10 to hardy.

---

### Post by EXCiD3 on 2008-05-16
Does opening Synaptic and doing "Fix broken packages" do anything?

---

### Post by pcglue on 2008-05-16
Solved.  

Fix this problem:
```
Setting up docbook-xml (4.5-5) ...
update-xmlcatalog: cannot open catalog data /var/lib/xml-core/docbook-xml for writing: No such file or directory at /usr/sbin/update-xmlcatalog line 485.
dpkg: error processing docbook-xml (--configure):
 subprocess post-installation script returned error exit status 2

```
by creating /var/lib/xml-core directory

Fixed this problem:
```

Setting up ttf-dejavu-core (2.23-1) ...
/etc/defoma/hints/ttf-dejavu-core.hints: Unable to open, or empty.
dpkg: error processing ttf-dejavu-core (--configure):
 subprocess post-installation script returned error exit status 1

```
by finding a copy of ttf-dejavu-core.hints on the web and copying it to /etc/defoma/hints.

Reran "dpkg --configure -a" and these packages and all their dependencies are OK now.  But don't know why it happened in the first place.

---

### Post by j8a on 2008-05-23
I succesfully upgrade from Gutsy a week ago, but I have problems with the synaptic package manager and other programs like Firefox. The run but not always, how could I run from the console the fix broken packages. Could you help me?

---

### Post by downforce on 2008-06-27
I had this same problem on a clean install of Hardy ...

I downloaded the .deb manually and extracted it using ar, copied the hints file to the relevant directory and continued the apt-get install.

All sweet :D

---

