---
title: "On installation, missing dependency -- libraptor1"
date: 2005-08-03
forum: Installation &amp; Upgrades
---

### Post by Jessehk on 2005-08-03
** I accidently posted this is the 4.10 section. I apologise. **
Okay, at initial install, Ubuntu told me it had problems with

librdf0 and librasqal10 because the were dependent on libraptor1

Therefore, it sent me to aptitude, where I tried to install libraptor1. It wouldn't let me.

Giving up ( after spending about 15 minutes on it ), I quit aptitude, and continued with the installation.

Everything works, as these seem to be just programming libraries, but I don't want broken packages on an initial install. It doesn't give a good first impression ( if you know what I mean. )

When I try to install libraptor1 with synaptic, I see the following message:

[http://images5.theimagehosting.com/Screenshot-Error.png](http://images5.theimagehosting.com/Screenshot-Error.png)
What do I do?

thanks

EDIT: here is the command line output
```


jesse@Jesse:~$ sudo apt-get install libraptor1
Reading package lists... Done
Building dependency tree... Done
Recommended packages:
  raptor-utils
The following NEW packages will be installed:
  libraptor1
0 upgraded, 1 newly installed, 0 to remove and 28 not upgraded.
5 not fully installed or removed.
Need to get 0B/112kB of archives.
After unpacking 311kB of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 59048 files and directories currently installed.)
Unpacking libraptor1 (from .../libraptor1_1.4.2-1_i386.deb) ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/libraptor1_1.4.2-1_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/doc/libraptor1/NEWS.gz')
Errors were encountered while processing:
 /var/cache/apt/archives/libraptor1_1.4.2-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This is an urgent problem, becuase apt is not allowing me to update anything without this package. 

Any help would be greatly appreciated to solve this big problem. 

thanks :)

---

