---
title: "apt-get fails to install packages after cutom install"
date: 2005-02-13
forum: Installation &amp; Upgrades
---

### Post by telematic on 2005-02-13
Hi,

I am new to ubuntu and debian, but I hope to make use of this distribution for my 3rd box at home. As the system only has 64mb at the moment I started to follow the from:
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

Basically I choose custom and following a tip from the ubuntu website after first reboot, when asked "Download Software from the Internet?" I said no.

Right, now I supposedly have a bare system working basic networking works fine and I can move around the system. I follow the first steps but when I try to start installing software, all fail with the following "not installable" error messages, for example icewm message below;

# apt-get install icewm
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  icewm: Depends: imlib1 but it is not installable
         Depends: libfontconfig1 (>= 2.2.1) but it is not installable
         Depends: libfreetype6 (>= 2.1.5-1) but it is not installable
         Depends: libice6 but it is not installable or
                  libjpeg62 but it is not installable
         Depends: libpng10-0 (>= 1.0.15-4) but it is not installable
         Depends: libsm6 but it is not installable or
                  libtiff4 but it is not installable
         Depends: libungif4g (>= 4.1.0b1) but it is not installable
         Depends: libx11-6 but it is not installable or
                  libxext6 but it is not installable or
                  libxft2 (> 2.1.1) but it is not installable
         Depends: libxrandr2 but it is not installable or
                  xlibs (> 4.3.0) but it is not installable
         Depends: libxrender1 but it is not installable
E: Broken packages


I have managed to install some packages like openssh-server and xserver-xfree86 but most of them fail with similar messages.

Any idea why I am getting this on a fresh installation? and most important how can I fix it?

All help will be greatly appreciated.

---

### Post by telematic on 2005-02-14
any ideas???

---

### Post by Xian on 2005-02-14
I'm not familiar with this install method, but I do know that the icewm meta-pkg command is valid in Warty's universe repos, so perhaps if you post your /etc/apt/sources.list contents there might be something amiss in that configuration that will come to light.

---

