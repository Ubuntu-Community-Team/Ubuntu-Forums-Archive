---
title: "VMware server install on ubuntu 10.10"
date: 2011-04-10
forum: Installation &amp; Upgrades
---

### Post by Neo@Matrix on 2011-04-10
Do anyone have experience with installing VMware server on Ubuntu 10.10 server x64 with GUI ?
Had no luck with this:

[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

most likely my bad.Any help appreciated.

The part where I stuck was:

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 


Seams to be about missing C compiler.

Any idea?

---

### Post by brandom on 2011-04-12
Hi,

  I'm trying to install vmware server on 10.10 too, and ending up with problems.  Actually, I've tried Workstation 7.1 (which at least installs) but that ended up getting stuck with a license number problem.

  Anyhow, for vmware server I followed [https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server) but the script dies:

```

Patching vmware-install.pl...
patching file ../vmware-server-distrib/bin/vmware-config.pl
Hunk #1 FAILED at 4121.
Hunk #2 FAILED at 4143.
2 out of 2 hunks FAILED -- saving rejects to file ../vmware-server-distrib/bin/vmware-config.pl.rej
Starting VMware Server original install script...
./vmware-server-2.0.x-kernel-2.6.3x-install.sh: line 319: ../vmware-server-distrib/vmware-install.pl: No such file or directory
Housekeeping...
Thank you for using the script!
Patch provided by: 
	Ramon de Carvalho Valle
	http://risesecurity.org
Script author: 
	Radu Cotescu
	http://radu.cotescu.com

```

So... I'm not sure what I can do.  I may try and contact the script author.

---

