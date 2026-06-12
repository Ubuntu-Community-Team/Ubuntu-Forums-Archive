---
title: "unable to open files list file for package..."
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by casperl on 2007-02-05
It all started when I attempted to install the latest Skype:

> casperl@casper-laptop:~/Desktop$ sudo dpkg -i skype_debian-1.3.0.53-1_i386.deb 
(Reading database ... dpkg: error processing skype_debian-1.3.0.53-1_i386.deb (--install):
 unable to open files list file for package `kexi': Input/output error
Errors were encountered while processing:
 skype_debian-1.3.0.53-1_i386.deb
Processing was halted because there were too many errors.


However, the problem lies with Kexi.  No matter what, I get the above errors.  I believe it is  because the previous (installed) Kexi had an strange or invalid filename: 

> kexi_1%3a1.5.2-0ubuntu2.1_i386.deb

No matter what I do, I hit against the "**unable to open files list file for package `kexi`: Input/output error**" message.  I have tried synaptic, aptitude and dpkg with the same (lack of) results.  I have attempted:

> sudo dpkg -r kexi
sudo dpkg -r kexi kexi-mdb-driver
sudo dpkg -P kexi kexi-mdb-driver
sudo dpkg --force-r kexi
sudo dpkg --force-P kexi kexi-mdb-driver
sudo dpkg -i kexi etc.

I have downloaded the 'better' kexi = **kexi_1.5.2-0ubuntu2.1_i386.deb** and tried to install / unpack that to no avail.

What else?  Just about anything I attempt with any package management tool provides the same error message above.

Any help will be appreciated.

TIA

---

### Post by casperl on 2007-02-06
what I discovered  is that there are a lot of invalid, 0 byte or funny files in one directory (and only that one directory)

> /var/lib/dpkg/info

There are more than 20 of them, all ending in the extension **-utils.list**

This is one of them

> ?--------- 2762 2744647680 181052216   33 1970-01-01 02:00 poppler-utils.list

And deleting the above file produces:

> sudo rm poppler-utils.list 
rm: remove write-protected weird file `poppler-utils.list'? Y
rm: cannot remove `poppler-utils.list': Operation not permitted

As a next step I am rebooting and performing a thorough filesystem check before anything else!

However, I am not so sure about a filesystem error such as a bad drive etc. since 1) Only this directory **/var/lib/dpkg/info** is affected and only files ending in **-utils.list** are affected.

Will post an update after the filesystem check.

---

### Post by casperl on 2007-02-20
The above errors continued.  Eventually it required a full backup and re-partition, re-install.

---

