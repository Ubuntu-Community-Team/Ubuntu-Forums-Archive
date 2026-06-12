---
title: "Still having trouble with dist-upgrade"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by Psquared on 2005-04-10
I need some help here.  ](*,) 

I'm running Warty and I've installed some stuff from backports, but I can't seem to upgrade to Hoary. I'm sure my sources.list file is wrong, but I don't know how to fix it.

Here it is:

> 
# deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 


## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe  
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe 

##deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main universe
##deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse 
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse 

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted 
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted 

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main 
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main 
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main 

# deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe 
# deb [ftp://neacm.fe.up.pt/pub/ubuntu-java/](ftp://neacm.fe.up.pt/pub/ubuntu-java/) binary/ 
# deb-src [ftp://neacm.fe.up.pt/pub/ubuntu-java/](ftp://neacm.fe.up.pt/pub/ubuntu-java/) source/ 

# deb [http://www.grawert.net/ubuntu/](http://www.grawert.net/ubuntu/) warty universe 

# deb [http://www.getsweaaa.com/~tseng/ubuntu/debs/](http://www.getsweaaa.com/~tseng/ubuntu/debs/) ./ 



I go through the process and it downloads the required files (takes about 90 minutes) and then instead of installing it gives me a series of messages about ALSA and bogofilter and then stops. I've tried restarting and running dist-upgrade again, but the same thing happens.

---

### Post by p!=f on 2005-04-10
Please, follow this thread:
[http://ubuntuforums.org/showthread.php?t=12174](http://ubuntuforums.org/showthread.php?t=12174)

---

