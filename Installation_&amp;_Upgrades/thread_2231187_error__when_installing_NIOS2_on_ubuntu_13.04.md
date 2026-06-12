---
title: "error / when installing NIOS2 on ubuntu 13.04"
date: 2014-06-24
forum: Installation &amp; Upgrades
---

### Post by Nguyen_Duc_Cuong on 2014-06-24
I DONT KNOW WHY MY POST IS CLOSED?

install sudo apt-get install ..... error / when installing NIOS2 on  ubuntu 13.04. I dont know why it happend, because i have installed and  updated all souces
>  	 		 			 			 				^[[Acuong@cuong-Vostro-3460:~$ sudo apt-get instgit-core git-gui  make gcc ncurses-dev bison flex gawk gettext ccache zlib1g-dev  libx11-dev texinfo liblzo2-dev pax-utils uboot-mkimage corkscrew
[sudo] password for cuong: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libncurses5-dev' instead of 'ncurses-dev'
gettext is already the newest version.
gcc is already the newest version.
make is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 liblzo2-dev : Depends: liblzo2-2 (= 2.06-1) but 2.06-1build1 is to be installed
 libncurses5-dev : Depends: libncurses5 (= 5.9-4) but 5.9-10ubuntu4 is to be installed
                   Depends: libtinfo-dev (= 5.9-4) but it is not going to be installed
                   Depends: ncurses-bin (= 5.9-4) but 5.9-10ubuntu4 is to be installed
 libx11-dev : Depends: libx11-6 (= 2:1.4.99.1-0ubuntu2.2) but 2:1.5.0-1ubuntu1 is to be installed
              Depends: libxau-dev (>= 1:1.0.0-1) but it is not going to be installed
              Depends: libxdmcp-dev (>= 1:1.0.0-1) but it is not going to be installed
              Depends: libxcb1-dev but it is not going to be installed
              Recommends: libx11-doc but it is not going to be installed
 zlib1g-dev : Depends: zlib1g (= 1:1.2.3.4.dfsg-3ubuntu4) but 1:1.2.7.dfsg-13ubuntu2 is to be installed
E: Unable to correct problems, you have held broken packages.
cuong@cuong-Vostro-3460:~$ 			 		

 	
 
Plz. help me for this!!!!!!!!!!!!!!!!!!

---

### Post by coffeecat on 2014-06-24
> **Nguyen_Duc_Cuong said:**
> I DONT KNOW WHY MY POST IS CLOSED?


The reason was clearly given in the closure note in post #3 of your other thread. Please read again:

[http://ubuntuforums.org/showthread.php?t=2231043](http://ubuntuforums.org/showthread.php?t=2231043)

Ubuntu 13.04 has been end of life since January this year. This means no updates. It will be very difficult if not impossible to solve your dependency problems in an unsupported version. You need to upgrade to a supported version of Ubuntu. I highly recommend that you consider a fresh installation of the current long-term support version 14.04 since 13.10 will itself become end of life very soon, and an upgrade to 13.10 could be very problematic considering those dependency issues.

If you need help with an upgrade (which I do not recommend), or a fresh install of 14.04, then you are welcome to start a new thread.

I am closing this now, because no one will be able to help you resolve this problem on an unsupported version of Ubuntu.

---

