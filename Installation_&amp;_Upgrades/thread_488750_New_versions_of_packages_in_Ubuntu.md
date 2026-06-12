---
title: "New versions of packages in Ubuntu"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by Inquisitive Alex on 2007-06-30
Kernel version in Ubuntu is 2.6.20-16, but the last one is 2.6.21.5. Will there be an update? The same question about Eclipse 3.3. How soon does new versions of packages usually appear?

---

### Post by Vajra Vrtti on 2007-06-30
New versions will come in new releases, i.e, they will come in Ubuntu 7.10.

---

### Post by Vajra Vrtti on 2007-06-30
Ubuntu 7.10 will use the 2.6.22 Linux kernel.

---

### Post by Inquisitive Alex on 2007-07-01
So, there is no chance to get new versions from Synaptic. The only way is to download and install software manually, right?

---

### Post by Vajra Vrtti on 2007-07-01
I think so. The packages in the repositories are supposed to work well together. If you put new versions in the repositories as soon as they are available the system as a whole may became unstable. The Ubuntu answer to that is to release stable new versions at predictable six months intervals. That works fine unless you terribly need some new feature of a package that is not yet in the current repositories. I did that with Azureus in Feisty. The best option is to find a deb package for the application because Synaptic will have control of it even if installed manually. Of course, whatever the installation method, be sure it comes from a site you can trust.

---

### Post by Vajra Vrtti on 2007-07-01
I'm sorry but what i said wasn't completely correct.

New versions of packages can be made available between Ubuntu releases. That is done in the backport repositories:

> 
**Ubuntu backports project**
The Ubuntu backports project provides packages from the development version, built for the latest stable release. This way you can mix stability with being on the bleeding edge. This repository is an official one, but should be used with care and only if you know what you are doing.

To use it, uncomment the appropriate lines in */etc/apt/sources.list*:

> ## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

---

### Post by Inquisitive Alex on 2007-07-02
Ok. Everything is clear now. Thank you.

---

### Post by snakyjake on 2007-07-11
The Backports don't seem to have the latest version of the very popular Thunderbird mail client and some other programs.  To me, this is a perfect and popular example of why the repositories are so confusing...at least to me.  I usually install from the binary, unless I have huge dependency problems.

If I have dependency problems it usually takes me days of install a bunch of stuff.  Sometimes it work, sometimes it never works until a release, and I'm always left wondering if I just installed a bunch of unneeded dependency junk trying to get something to work.

Going to a distribution that utilizes RPM's might be a better alternative.  Download the newest version of something, and then install.  No need to wait 6 months, nor wait for a backport, and maybe not the hassle with installing from binary.  I've hear you can use Alien to install RPM's on Debian machines, so this might be an option, but I haven't had much luck with it.

I want to install things easily, just like I do in Windows with the MSI installer.

If anyone has any news about a new package management system, please send me a link.  I'm interested to hear about any improvements in this area.

---

