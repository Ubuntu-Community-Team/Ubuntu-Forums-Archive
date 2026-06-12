---
title: "broken apt-get/synaptic - python installation suspected"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by danzinho on 2007-02-28
Dear all

My apt-get/aptitude/synaptic system has become broken.  I think the problem goes back to when I tried to install some Python-related extra packages.

The immediate symptom of this is

The following packages have unmet dependencies:
  libgnomevfs2-0: Depends: libgnomevfs2-common (= 2.16.1-0ubuntu7) but 2.16.1-0ubuntu6 is installed and it is kept back.
  libgnomevfs2-extra: Depends: libgnomevfs2-common (= 2.16.1-0ubuntu7) but 2.16.1-0ubuntu6 is installed and it is kept back.

This actually has irritating, but non-fatal, consequences for removable disk usage, but the main problem is that the underlying Python problem (I think) affects installation of lots of things. I get this

daniel@adenine:~/str_biol_group$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  libplot2c2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgnomevfs2-common
The following packages will be upgraded:
  libgnomevfs2-common
1 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
5 not fully installed or removed.
Need to get 0B/651kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 140972 files and directories currently installed.)
Preparing to replace libgnomevfs2-common 2.16.1-0ubuntu6 (using .../libgnomevfs2-common_2.16.1-0ubuntu7_all.deb) ...
Unpacking replacement libgnomevfs2-common ...
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 11, in ?
    import os
ImportError: No module named os
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 11, in ?
    import os
ImportError: No module named os
dpkg: error processing /var/cache/apt/archives/libgnomevfs2-common_2.16.1-0ubuntu7_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 11, in ?
    import os
ImportError: No module named os
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libgnomevfs2-common_2.16.1-0ubuntu7_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


The repeated 'ImportError: No module named os' messages make me suspect Python, and others have seen this
[http://www.linuxquestions.org/questions/showthread.php?t=433460](http://www.linuxquestions.org/questions/showthread.php?t=433460)

What to try next?  Deinstalling then reinstalling all Python seems a non-starter since, according to Synaptic, zillions of other things depend on it.

I really appreciate your help

Daniel

---

### Post by bapoumba on 2007-02-28
> **danzinho said:**
> 
The following packages have unmet dependencies:
  libgnomevfs2-0: Depends: libgnomevfs2-common (= 2.16.1-0ubuntu7) but 2.16.1-0ubuntu6 is installed and it is kept back.
  libgnomevfs2-extra: Depends: libgnomevfs2-common (= 2.16.1-0ubuntu7) but 2.16.1-0ubuntu6 is installed and it is kept back.

Hello :)

Not sure I can help you out, but where did you get libgnomevfs2-common 2.16.1-0ubuntu6 from ?

Current edgy version is 2.16.1-0ubuntu7 and dapper is 2.14.1-0ubuntu8.

What is the output to **cat /etc/apt/sources.list** ?

---

### Post by danzinho on 2007-03-01
> **bapoumba said:**
> Hello :)

Not sure I can help you out, but where did you get libgnomevfs2-common 2.16.1-0ubuntu6 from ?

Current edgy version is 2.16.1-0ubuntu7 and dapper is 2.14.1-0ubuntu8.

What is the output to **cat /etc/apt/sources.list** ?

Hi!

The output is this

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free                                               
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

## Listen
#deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) edgy listen


Does that help pin down the problem at all?

Thanks

Daniel

---

