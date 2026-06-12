---
title: "package uses Breaks; not supported in this dpkg"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by Spuds on 2007-04-27
Trying a dist-upgrade to feisty-- downloaded all of the packages and then complains with the following error:


After unpacking 254kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: regarding .../udev_108-0ubuntu4_i386.deb containing udev:
 package uses Breaks; not supported in this dpkg
dpkg: error processing /var/cache/apt/archives/udev_108-0ubuntu4_i386.deb (--unpack):
 unsupported dependency problem - not installing udev
Errors were encountered while processing:
 /var/cache/apt/archives/udev_108-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Mind you... this is the output of an apt-get -f install to try and resolve the problem... but this is the original problem.

Clean 6.10 system (aside from sysvinit problems outlined in a previous post)... 

Spuds

---

### Post by sehe on 2007-06-09
I'm having exactly the same issues form a Feisty install (no upgrade)

I have seen the sysvinit issues before as well. Seems that thsi break something really bad.

I tried reinstalling initramfs-tools because after a rgular (automatic!!!) kernel upgrade my system wouldnt boot with 'Init not found' messages and a perfect grub config. Also, previous kernel would still work, new kernel would load (of course with many errors) against the old initrd -> making me think initrd was the problem. 

I hadn't found out about update-initrd yet, but it seems now I never will because i cannot re-install udev once it has been removed :)

Looks like I'm headed for a full reinstall of Feisty.

Have you got news?

---

### Post by KeithBarney on 2007-07-04
I just fixed this error on a Feisty upgrade by grabbing the 1.14.4 version of dpkg from here: [http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/](http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/) .  The newer dpkg seems to know what do when it sees a package that uses Breaks.  When I was installing it I had to force the old version of dpkg to install the new version of dpkg with the --force parameter.  I also grabbed the 1.14.4 version of dpkg-dev from the same place.

Maybe this will work for you too...

-Keith Barney

---

