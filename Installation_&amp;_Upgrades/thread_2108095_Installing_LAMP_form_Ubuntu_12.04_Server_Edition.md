---
title: "Installing LAMP form Ubuntu 12.04 Server Edition"
date: 2013-01-23
forum: Installation &amp; Upgrades
---

### Post by empollondefisica on 2013-01-23
I'm currently trying to do a LAMP install by way of using the Ubuntu 12.04 Server install disk.  None of the computers have (or will have) an Internet connection, and I have had very little luck in tracking down all the dependencies to download the individual packages.

I have added the Ubuntu 12.04 Server CD in Software Sources.

The command: **sudo apt-get -y install apache2** lists the packages that are going to be installed and tries to begin, but then I get this error:

```

Media change: please insert the disc labeled
  'Ubuntu-Server 12.04.1 LTS _Precise Pengolin_ -Release i386 (201220817.3)'
in the drive '/media/cdrom/' and press enter

```

I checked the mount point of the CD and found that it was **/media/Ubuntu-Server...**

Explicitly mounting the CD to /media/cdrom/ did not help either because (I assume) apt-get merely dismounted it and printed the error again.

Is there any way to force apt-get to look in a different filepath to find the CD?

---

### Post by empollondefisica on 2013-01-23
I managed to get around my issue by copying all the packages into a local directory and creating a local repository following these instructions: [How To Build Local APT Repositories]("http://odzangba.wordpress.com/2006/10/13/how-to-build-local-apt-repositories/")

While it wasn't really the solution I wanted, it achieves a close-enough result.

As such I'm marking this thread **SOLVED**

---

