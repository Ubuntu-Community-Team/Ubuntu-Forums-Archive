---
title: "broken packages causing Synaptic hangup"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by tchoklat on 2006-10-30
Whilst attempting to update with Synaptic I get a message that a package is corrupt, running the following command, sudo apt-get install -f this is tyhe output.

Synaptic will not allow me to upgrade without fixing the error. I am unable to delete or upgrade the package - which I do not need by the way.



******************:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/2904kB of archives.
After unpacking 123kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 103485 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.1 (using .../samba_3.0.22-1ubuntu4_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu4_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Hope some-one can help

---

### Post by BLTicklemonster on 2006-11-01
Like bump already, dude needs help, ya'll.

---

### Post by Neoito on 2006-11-08
Bump, since having same problem and can't seem to fix.

---

### Post by robenroute on 2006-11-28
> **Neoito said:**
> Bump, since having same problem and can't seem to fix.

Same here. Is there any documentation on this matter? I don't mind reading up on it or fiddling with it. man and info pages are definitely not sufficient.

Thanks, Rob

---

### Post by bapoumba on 2006-11-28
The original bug report :
[https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/9208]("https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/9208")

One on edgy :
[URL="https://launchpad.net/distros/ubuntu/+source/samba/+bug/68378"]
https://launchpad.net/distros/ubuntu/+source/samba/+bug/68378[/URL]
There is a workaround. Hope this helps.

---

### Post by BLTicklemonster on 2006-11-28
Okay, so it happened to me, and finally I got it taken care of, though it may or may not work for you, and may or may not have consequences that could possibly be detrimental to your primary goal, though it took care of the broken packages.

sudo aptitude update

sudo aptitude upgrade


You will be given choices along the way that ought to help you to clean up problems.

and if not, just pick something from synaptic that you can install from terminal (not synaptic) and 

sudo aptitude install whatever

This is not a "do this because it is what you should do" kind of post. Rather, it's a "hey, this worked for me and I don't have any problems anymore as a result of doing it" post. I really don't see where it could cause any severe problems unless perhaps your kernel is the problem.

---

