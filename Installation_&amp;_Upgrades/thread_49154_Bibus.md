---
title: "Bibus"
date: 2005-07-15
forum: Installation &amp; Upgrades
---

### Post by kayas80 on 2005-07-15
Hi everyone

I'm a linux and ubuntu newbie so please go easy. I am trying to install Bibus to no avail. I've added the required repositiries to sources.list and tried installing from synaptic but it says: "Depends: python (<2.4) but 2.4.1-0ubuntu2 is to be installed".

I then tried using the guidelines from sourceforge for Debian ([http://bibus-biblio.sourceforge.net/html/en/introduction.html#mozTocId157381](http://bibus-biblio.sourceforge.net/html/en/introduction.html#mozTocId157381)) but again to no avail.  ](*,)  This is the error message I get when installing from the terminal: -

kayas80@kayas80:~$ sudo apt-get install bibus bibus-doc-en openoffice-pyuno
Reading package lists... Done
Building dependency tree... Done
bibus-doc-en is already the newest version.
openoffice-pyuno is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  bibus: Depends: python (< 2.4) but 2.4.1-0ubuntu2 is to be installed
E: Broken packages


Here is a copy of my sources.list: -

## Uncomment the following two lines to fetch updated software from the network
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse universe main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

## Bibus
deb [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio) ./
deb-src [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio) ./


Any help anyone could offer would be greatly appreciated. Many thanks in advance.

Oliver

---

