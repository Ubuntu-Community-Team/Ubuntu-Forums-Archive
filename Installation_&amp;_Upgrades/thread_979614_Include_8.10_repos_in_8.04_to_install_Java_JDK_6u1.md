---
title: "Include 8.10 repos in 8.04 to install Java JDK 6u10"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by IanWood on 2008-11-12
Hi,

I am using 8.04 at work and want to install Java JDK 6u10. In the repos the newest version is 6u7. 

However at home I use 8.10 and the repos have 6u10.

How can I get my 8.04 Ubuntu to be able to "see" the Java JDK 6u10 that my 8.10 Ubuntu sees?

BTW, I can't upgrade to 8.10 at work as the newer Xorg doesn't work the Matrox video card. I have already upgraded to 8.10 and then reinstalled 8.04...

Cheers

Ian

---

### Post by jamesstansell on 2008-12-12
> **IanWood said:**
> Hi,

I am using 8.04 at work and want to install Java JDK 6u10. In the repos the newest version is 6u7. 

However at home I use 8.10 and the repos have 6u10.

How can I get my 8.04 Ubuntu to be able to "see" the Java JDK 6u10 that my 8.10 Ubuntu sees?

BTW, I can't upgrade to 8.10 at work as the newer Xorg doesn't work the Matrox video card. I have already upgraded to 8.10 and then reinstalled 8.04...

Cheers

Ian

Hi Ian,

What I did was download the .deb files from launchpad.net and installed them using the dpkg -i command.

(This works with the sun-java packages because they are the exact binaries that Sun created, and they created them to work across most Linux versions.  In general mixing packages like this from different ubuntu versions is a bad idea and won't work out.  For the general case you would want to request that backported packages be created.)

You could also copy the files from the apt cache on your home machine or download them from packages.ubuntu.com, packages.debian.org, directly from a server in your sources.list file, or possibly other places.  There are probably techniques with apt, apt-cacher or other tools that would keep you from having to manually download and install them.

Just wondering - is there anything in particular about 6u10 that you want to use?  Also 6u11 was released to fix about 14 security bugs, so to get the very latest release you might want to snag it from the jaunty (ubuntu 9.04) repository.

---

