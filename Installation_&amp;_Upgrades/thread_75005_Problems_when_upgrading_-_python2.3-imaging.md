---
title: "Problems when upgrading - python2.3-imaging"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by wezzer-foo on 2005-10-13
Hi all

I'm trying to upgrade from hoary to breezy and big problems appeared.
sudo apt-get dist-upgrade didn't manage to install python2.4-imaging and wanted me to run command:
sudo apt-get install -f
When I run that, I get following message:

> Preconfiguring packages ...
(Reading database ... 109915 files and directories currently installed.)
Unpacking python2.4-imaging (from .../python2.4-imaging_1.1.5-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/python2.4-imaging_1.1.5-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/bin/pilconvert.py', which is also in package python2.3-imaging
Errors were encountered while processing:
 /var/cache/apt/archives/python2.4-imaging_1.1.5-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

sudo apt-get remove --purge python2.3-imaging or python2.4-imaging won't help. :/

I'm out of ideas.

---

### Post by shinygerbil on 2005-10-13
I got something very similar with the file openoffice.org2-help-en-us... It would be very useful if comeone could find a way of skipping its installation. I've tried looking through the manual, but no dice - is there any way of just skipping one .deb file and carrying on with the installation of everything else? Nothing else has installed, I'm left with the unix shell.. :(

Any advice would be most welcome, thanks in advance!

Steve

---

### Post by shinygerbil on 2005-10-13
Solved it! Using aptitude is much better :)

I typed:
```
# aptitude dist-upgrade
```
It started to download the packages but didn't try and install anything.
Then I typed:
```
# aptitude hold openoffice.org-help-en-us
```
and, as if by magic, it proceeded to upgrade without any further hitches!

---

### Post by wezzer-foo on 2005-10-14
I solved problems also. I had several packages which had this same problem. Here is the solution

> sudo apt-get remove python2.4-imaging
and delete all packages which it wants.
then
> sudo apt-get install -f
and
> sudo apt-get dist-upgrade
and so on...

And this same procedure has to be made to all problem packages - it took 4 hours to me, but now Breezy is working perfectly.

---

