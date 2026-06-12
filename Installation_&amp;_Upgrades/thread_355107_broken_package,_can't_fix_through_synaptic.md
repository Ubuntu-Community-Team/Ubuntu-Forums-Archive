---
title: "broken package, can't fix through synaptic"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by lavaface on 2007-02-06
After installing upgrades today, my package manager tells me I have a broken package, and when I use synaptic to find it, samba, I can't upgrade it.  Doesn't work through the command line either.  In case you can't tell, I don't really know what I'm doing here.  

This is the error synaptic gives me when I try to upgrade the broken package:
E: /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb: subprocess new pre-removal script returned error exit status 102

And this is what the command line tells me:
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

My linux guru is out of town, and I am clueless as to how to fix this, or even if it's something I should worry about.  Sorry if this isn't in the correct forum.

---

### Post by moshuptrail on 2007-02-06
I've got the same problem.  Doing a sudo apt-get install -f shows:

```
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2845kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: unable to initialize frontend: Kde
debconf: (Unable to load Qt -- is libqt-perl installed?)
debconf: falling back to frontend: Dialog
Preconfiguring packages ...
(Reading database ... 90151 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.1 (using .../samba_3.0.22-1ubuntu3.2_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by p!=f on 2007-02-06
Maybe this
[https://launchpad.net/ubuntu/+source/samba/+bug/68378](https://launchpad.net/ubuntu/+source/samba/+bug/68378)
and this
[https://answers.launchpad.net/ubuntu/+ticket/1556](https://answers.launchpad.net/ubuntu/+ticket/1556)
helps.

---

### Post by moshuptrail on 2007-02-06
Not exactly, (the answer there is for dapper->edgy) but the answer here is about the same:

[http://www.ubuntuforums.org/showthread.php?t=240699&highlight=exit+status+102](http://www.ubuntuforums.org/showthread.php?t=240699&highlight=exit+status+102)

---

### Post by lavaface on 2007-02-06
That worked, thanks so much!

---

### Post by Lucas2005 on 2007-02-08
That worked for me too.  I no longer have Samba registered as "Broken"  I did not test samba to make sure it worked...

---

### Post by borris.morris on 2007-02-17
I had an exit error one and it was because of a bad smb.conf

---

