---
title: "help on getting synaptic back!!!"
date: 2005-02-26
forum: Installation &amp; Upgrades
---

### Post by fengergold on 2005-02-26
I went from warty to hoary. on the way i lost synaptic. i tried to "sudo apt-get install synaptic" but it failed. what should i do??? 
here is the result fom the terminal:

$ sudo apt-get install synaptic
Password:
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
  synaptic: Depends: libapt-pkg-libc6.3-5-3.3
E: Broken packages
 ](*,) 


I am running ubuntu on a sony vaio PCG-Z600TEK

---

### Post by p!=f on 2005-02-26
Post your /etc/apt/sources.list here.
Where is the libapt-pkg-libc6.3-5-3.3 package from?

---

### Post by alastair on 2005-02-26
How did you go from warty to hoary?

It looks like there's a C library problem - which could be dangerous to play around with. If I look at my synaptic (hoary dev tracking - never been warty), I see :

Dependencies: ... libapt-pkg-libc6.3-5-3.9 ....

My libc installation (dpkg -l "libc*" | grep '^ii') is :

ii  libc6          2.3.2.ds1-20ub GNU C Library: Shared libraries and Timezone
ii  libc6-dev      2.3.2.ds1-20ub GNU C Library: Development Libraries and Hea
ii  libc6-i686     2.3.2.ds1-20ub GNU C Library: Shared libraries [i686 optimi

---

### Post by fengergold on 2005-02-27
[QUOTE=p!=f]Post your /etc/apt/sources.list here.
Where is the libapt-pkg-libc6.3-5-3.3 package from?[/QUOTE]

i have no idea where  libapt-pkg-libc6.3-5-3.3 package is from or what it is. I am still new in Ubuntu town and trying to learn...

This is my current /etc/apt/sources.list
START
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse 

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main 

deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe  
END



THANX fenger

---

### Post by fengergold on 2005-02-27
[QUOTE=alastair]How did you go from warty to hoary?

It looks like there's a C library problem - which could be dangerous to play around with. If I look at my synaptic (hoary dev tracking - never been warty), I see :

Dependencies: ... libapt-pkg-libc6.3-5-3.9 ....

My libc installation (dpkg -l "libc*" | grep '^ii') is :

ii  libc6          2.3.2.ds1-20ub GNU C Library: Shared libraries and Timezone
ii  libc6-dev      2.3.2.ds1-20ub GNU C Library: Development Libraries and Hea
ii  libc6-i686     2.3.2.ds1-20ub GNU C Library: Shared libraries [i686 optimi[/QUOTE]


i changed from warty to hoary by changing /etc/apt/sources.list
the word warty to hoary. my linux skills are not yet on the level that i would understand what i can use the information above for so please go slow (sorry i am trying trying trying)
 :?  fengergold

---

