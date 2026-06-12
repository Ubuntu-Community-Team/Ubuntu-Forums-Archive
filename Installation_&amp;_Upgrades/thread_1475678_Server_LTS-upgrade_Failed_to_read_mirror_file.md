---
title: "Server LTS-upgrade: Failed to read mirror file"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by Deviant1 on 2010-05-07
Hi,

I'm trying to upgrade an ubuntu server (Hardy Heron) to the new LTS Lucid.
I did a apt-get update & apt-get upgrade, I set the prompt=LTS in the release-upgrades-file and when I execute do-release-upgrade (I tried --proposed & --devel-release), I get the following error:

```

root@pec:~# do-release-upgrade --proposed
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
extracting 'lucid.tar.gz'
authenticate 'lucid.tar.gz' against 'lucid.tar.gz.gpg' 
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
tar: Removing leading `/' from member names

Reading cache

Checking package manager
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
Done downloading            
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
No candidate ver:  linux-image-2.6.15-26-amd64-server
No candidate ver:  libldap-2.2-7
No candidate ver:  libkpathsea3
No candidate ver:  xclock
No candidate ver:  linux-image-2.6.24-22-server
No candidate ver:  ntp-simple
No candidate ver:  libisc11
No candidate ver:  linux-image-2.6.15-28-amd64-server
No candidate ver:  libzzip-0-12
No candidate ver:  netkit-inetd
No candidate ver:  libdns21
No candidate ver:  xmore
No candidate ver:  libisccfg1
No candidate ver:  modutils
No candidate ver:  xrgb
No candidate ver:  xconsole
No candidate ver:  xman
No candidate ver:  xmag
No candidate ver:  libgnutls11
No candidate ver:  libnewt0.51
No candidate ver:  linux-image-2.6.24-19-server
No candidate ver:  initrd-tools
No candidate ver:  libgmpxx3
No candidate ver:  libneon24
No candidate ver:  libneon25
No candidate ver:  xditview
No candidate ver:  xvidtune
No candidate ver:  libnfsidmap1
No candidate ver:  viewres
No candidate ver:  libc-client2002edebian
No candidate ver:  xlogo
No candidate ver:  lvm-common
No candidate ver:  xfontsel
No candidate ver:  xcalc
No candidate ver:  xgc
No candidate ver:  php4-common
No candidate ver:  libdevmapper1.02
No candidate ver:  libisccc0
No candidate ver:  libbind9-0
No candidate ver:  linux-image-2.6.24-23-server
No candidate ver:  ncftp2
No candidate ver:  xmessage
No candidate ver:  xload
No candidate ver:  libreadline4
No candidate ver:  imake
No candidate ver:  libmysqlclient12
No candidate ver:  libmysqlclient10
No candidate ver:  libmysqlclient14
No candidate ver:  xsm
No candidate ver:  libmagick9
No candidate ver:  tetex-doc
No candidate ver:  libparted1.6-13
No candidate ver:  libapr0
No candidate ver:  bitchx
No candidate ver:  linux-image-2.6.15-51-amd64-server
No candidate ver:  libglib1.2
No candidate ver:  linux-image-2.6.15-29-amd64-server
No candidate ver:  liblwres9
No candidate ver:  beforelight
No candidate ver:  bitmap
No candidate ver:  ipchains
No candidate ver:  ntp-server
No candidate ver:  linux-image-2.6.24-21-server
No candidate ver:  oclock
No candidate ver:  libpoppler1
No candidate ver:  editres
No candidate ver:  xfd
No candidate ver:  xclipboard
No candidate ver:  libsvn0
No candidate ver:  libjasper-1.701-1

Updating repository information
WARNING: Failed to read mirror file
Done downloading            

Checking package manager
Reading package lists: Donem lucid-security/multiverse Packages: 96   
Reading state information: Done
Reading state information: Done
Reading state information: Done

Calculating the changes

Calculating the changes

Could not calculate the upgrade 

An unresolvable problem occurred while calculating the upgrade: 
E:Unable to correct problems, you have held broken packages. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug against the 
'update-manager' package and include the files in 
/var/log/dist-upgrade/ in the bug report. 


Restoring original system state

Aborting
Reading package lists: Donem hardy-security/multiverse Packages: 96   
Reading state information: Done
Reading state information: Done
Reading state information: Done

```

Can anybody help me with this?

Thanks in advance

---

### Post by dino99 on 2010-05-07
***** An unresolvable problem occurred while calculating the upgrade: 
E:Unable to correct problems, you have held broken packages. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug against the 
'update-manager' package and include the files in 
/var/log/dist-upgrade/ in the bug report. *********

so you need to check the sources.list and maybe "comment" some ppa or third party, then clean the cache, update and run install -f.

Then try to upgrade with the genuine lucid repo only by updating the sources.list directly. Later you may need to search updating your extra repo.

---

### Post by Deviant1 on 2010-05-08
Thanks for the reply.
I found out what the problem was. I removed all obsolete packages and then he could proceed with the installation.

---

