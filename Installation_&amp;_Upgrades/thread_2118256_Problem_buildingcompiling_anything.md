---
title: "Problem building/compiling anything"
date: 2013-02-20
forum: Installation &amp; Upgrades
---

### Post by robawalsh on 2013-02-20
I'm getting these error when I try to compile anything:

robawalsh@Dell-Inspiron-N5110:/media/DATA/Linux/drivers/wireless/hybrid-portsrc_x86_64-v5_100_82_112$ make KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd` make[1]: Entering directory `/usr/src/linux-headers-3.2.0-38-generic' Wireless Extension is the only possible API for this kernel version Using Wireless Extension API   LD      /media/DATA/Linux/drivers/wireless/hybrid-portsrc_x86_64-v5_100_82_112/built-in.o   CC [M]  /media/DATA/Linux/drivers/wireless/hybrid-portsrc_x86_64-v5_100_82_112/src/shared/linux_osl.o   CC [M]  /media/DATA/Linux/drivers/wireless/hybrid-portsrc_x86_64-v5_100_82_112/src/wl/sys/wl_linux.o /media/DATA/Linux/drivers/wireless/hybrid-portsrc_x86_64-v5_100_82_112/src/wl/sys/wl_linux.c:388:2: error: unknown field &#8216;ndo_set_multicast_list&#8217; specified in initialiser /media/DATA/Linux/drivers/wireless/hybrid-portsrc_x86_64-v5_100_82_112/src/wl/sys/wl_linux.c:388:2: warning: initialisation from incompatible pointer type [enabled by default] /media/DATA/Linux/drivers/wireless/hybrid-portsrc_x86_64-v5_100_82_112/src/wl/sys/wl_linux.c:388:2: warning: (near initialisation for &#8216;wl_netdev_ops.ndo_validate_addr&#8217;) [enabled by default] make[2]: *** [/media/DATA/Linux/drivers/wireless/hybrid-portsrc_x86_64-v5_100_82_112/src/wl/sys/wl_linux.o] Error 1 make[1]: *** [_module_/media/DATA/Linux/drivers/wireless/hybrid-portsrc_x86_64-v5_100_82_112] Error 2 make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-38-generic' make: *** [all] Error 2

I need to be able to compile now because I'm trying to install wireless drivers.
  I have run sudo apt-get update && sudo apt-get upgrade.

---

### Post by MAFoElffen on 2013-02-20
Looks like a depends problem...

You didn't say what version Ubuntu you are running or what specific driver, but for most wireless drivers on 12.04 LTS and running 64bit (looked at your errors and saw 64bit errors):
```

sudo apt-get install build-essential gcc-4.5 g++-4.5 ia32-libs libxi-dev libxmu-dev freeglut3-dev subversion libncurses5-dev zlib1g-dev gawk gcc-multilib flex git-core gettext fakeroot dh-make debhelper  debconf wget execstack

```
Would cover you for most everything a normal person would need to compile on a 64bit system. Anything already installed on your system, it would just skip.

"build-essentials" (and add "ialibs-32" for 64bit systems) is  the main package that almost everyone needs to install before compiling something on their own in Ubuntu for NIC drivers, graphics binaries, etc., etc. The making sure the compilers are up to a certain version. Then libraries specific to what it is compiling.

Hope this helps.

---

### Post by ajgreeny on 2013-02-20
Have you installed the build-essentials package that is needed to compile and install anything?
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by robawalsh on 2013-02-20
> **MAFoElffen said:**
> Looks like a depends problem...

You didn't say what version Ubuntu you are running or what specific driver, but for most wireless drivers on 12.04 LTS and running 64bit (looked at your errors and saw 64bit errors):
```

sudo apt-get install build-essential gcc-4.5 g++-4.5 ia32-libs libxi-dev libxmu-dev freeglut3-dev subversion libncurses5-dev zlib1g-dev gawk gcc-multilib flex git-core gettext fakeroot dh-make debhelper  debconf wget execstack

```Would cover you for most everything a normal person would need to compile on a 64bit system. Anything already installed on your system, it would just skip.

"build-essentials" (and add "ialibs-32" for 64bit systems) is  the main package that almost everyone needs to install before compiling something on their own in Ubuntu for NIC drivers, graphics binaries, etc., etc. The making sure the compilers are up to a certain version. Then libraries specific to what it is compiling.

Hope this helps.

Yes I have installed build-essentials. 

Here's the response: 
```

robawalsh@Dell-Inspiron-N5110:~$ sudo apt-get install build-essential gcc-4.5 g++-4.5 ia32-libs libxi-dev libxmu-dev freeglut3-dev subversion libncurses5-dev zlib1g-dev gawk gcc-multilib flex git-core gettext fakeroot dh-make debhelper  debconf wget execstack
[sudo] password for robawalsh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
debconf is already the newest version.
debhelper is already the newest version.
debhelper set to manually installed.
fakeroot is already the newest version.
fakeroot set to manually installed.
gawk is already the newest version.
gawk set to manually installed.
gettext is already the newest version.
gettext set to manually installed.
git-core is already the newest version.
libxi-dev is already the newest version.
libxi-dev set to manually installed.
wget is already the newest version.
zlib1g-dev is already the newest version.
zlib1g-dev set to manually installed.
build-essential is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 ia32-libs : Depends: ia32-libs-multiarch
E: Unable to correct problems, you have held broken packages.
robawalsh@Dell-Inspiron-N5110:~$ 

```

I don't know what the "you have held broken packages" means, or which packages are broken, and I tried "Fix broken packages" in Synaptic but that appeared to do nothing...

---

### Post by MAFoElffen on 2013-02-20
> **robawalsh said:**
> Yes I have installed build-essentials. 

The following packages have unmet dependencies.
 ia32-libs : Depends: ia32-libs-multiarch
E: Unable to correct problems, you have held broken packages.
robawalsh@Dell-Inspiron-N5110:~$ 
[/CODE]

I don't know what the "you have held broken packages" means, or which packages are broken, and I tried "Fix broken packages" in Synaptic but that appeared to do nothing...
Try this:
```

sudo apt-get install -f

```
And which version Ubuntu and what specific driver?

---

### Post by robawalsh on 2013-02-20
> **MAFoElffen said:**
> Try this:
```

sudo apt-get install -f

```And which version Ubuntu and what specific driver?[B]

sudo apt-get install -f[/B] didn't help

I'm running Ubuntu 12.04 LTS kernel 3.2.0-38-generic

Specifically, I was trying to compile and install the official Broadcom STA 802.11 driver, but this problem also happened when trying to compile other drivers, like brcmscmac (brcm80211), and basically anything I've tried to compile

---

### Post by MAFoElffen on 2013-02-20
> **robawalsh said:**
> [B]

sudo apt-get install -f[/B] didn't help

I'm running Ubuntu 12.04 LTS kernel 3.2.0-38-generic

Specifically, I was trying to compile and install the official Broadcom STA 802.11 driver, but this problem also happened when trying to compile other drivers, like brcmscmac (brcm80211), and basically anything I've tried to compile
Try this for the latest problem:
```

sudo apt-get install ia32-libs ia32-libs-multiarch

```
Looking at the source that you are installing and seeing if it sheds any light... Wait one on that.

---

### Post by robawalsh on 2013-02-20
> **MAFoElffen said:**
> Try this for the latest problem:
```

sudo apt-get install ia32-libs ia32-libs-multiarch

```Looking at the source that you are installing and seeing if it sheds any light... Wait one on that.
Yeah I tried that, same error: 
```

robawalsh@Dell-Inspiron-N5110:~$ sudo apt-get install ia32-libs ia32-libs-multiarch
[sudo] password for robawalsh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 ia32-libs-multiarch:i386 : Depends: gstreamer0.10-plugins-good:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by MAFoElffen on 2013-02-20
That particular source should depend on: build-essential, debhelper, dh-apparmor, difstat, dpkg-dev, g++, g++-4.6, gettext, html2text, initool-debian, libalgorithm-diff-perl, libalgorithm-diff-xs-perl, libalgorithm-merge-perl, libdkg-perl, libstd++6-4.6-dev, module-assistant, po-debconf and quilt.

While I was looking up the source you said you are trying to compile for that driver...I found ubuntu package broadcom-sta-common.

"broadcom-sta-common" is a binary-only device driver to support the following IEEE 802.11a/b/g/n wireless network cards: BCM4311-, BCM4312-, BCM4313-, BCM4321-, BCM4322-, BCM43224-, BCM43225-, BCM43227-, and BCM43228-based hardware.

If you install that broadcom-sta-common package, it also installs all those above depends, plus broadcom-sta-source... and since it's in the repo's, it would update automatically as new versions become available...

That is now two routes...

---

### Post by robawalsh on 2013-02-20
> **MAFoElffen said:**
> That particular source should depend on: build-essential, debhelper, dh-apparmor, difstat, dpkg-dev, g++, g++-4.6, gettext, html2text, initool-debian, libalgorithm-diff-perl, libalgorithm-diff-xs-perl, libalgorithm-merge-perl, libdkg-perl, libstd++6-4.6-dev, module-assistant, po-debconf and quilt.

While I was looking up the source you said you are trying to compile for that driver...I found ubuntu package broadcom-sta-common.

"broadcom-sta-common" is a binary-only device driver to support the following IEEE 802.11a/b/g/n wireless network cards: BCM4311-, BCM4312-, BCM4313-, BCM4321-, BCM4322-, BCM43224-, BCM43225-, BCM43227-, and BCM43228-based hardware.

If you install that broadcom-sta-common package, it also installs all those above depends, plus broadcom-sta-source... and since it's in the repo's, it would update automatically as new versions become available...

That is now two routes...

Yes but I'm trying to install the drivers manually since the broadcom-sta-common package isn't working - that's a separate issue here: [http://ubuntuforums.org/showthread.php?p=12521161](http://ubuntuforums.org/showthread.php?p=12521161)

broadcom-sta-common is installed, as well as broadcom-sta-source and bcmwl-kernel-source 

The focus of this thread was the compiling issue which keeps recurring when I try to compile anything...

---

### Post by MAFoElffen on 2013-02-20
okay-
```

sudo apt-get remove ia32-libs ia32-libs-multiarch

```
Then go to synaptic > search on ia32-libs > mark that for install and it "should" mark all the depends under that to resolve it.

It's a common package that most 64bit users need to install driver & other packages... You're going to need it eventually.

That is strange. As I installed that same ia32-lib package on 3 64bit systems within the last 4 days ago with no errors...

I see. Can agree on the manual compile if it had problems somewhere in the package. That would triage if is an Ubuntu package problem or if the problem still exists on Broadcom source. Then it would be an upstream Broadcom problem. That is what I'd say/comment to try if I saw it on launchpad.

---

### Post by robawalsh on 2013-02-20
> **MAFoElffen said:**
> okay-
```

sudo apt-get remove ia32-libs ia32-libs-multiarch

```Then go to synaptic > search on ia32-libs > mark that for install and it "should" mark all the depends under that to resolve it.

It's a common package that most 64bit users need to install driver & other packages... You're going to need it eventually.


```
robawalsh@Dell-Inspiron-N5110:~$ sudo apt-get remove ia32-libs ia32-libs-multiarch
[sudo] password for robawalsh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ia32-libs is not installed, so not removed
Package ia32-libs-multiarch:i386 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
robawalsh@Dell-Inspiron-N5110:~$ 
```And in Synaptic, I marked ia32-libs to install, it found the dependencies, I clicked Install but it gave me: 

*The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the 'Repositories' option under 'Settings'. *
     ia32-libs:
 Depends: ia32-libs-multiarch


...which they are.


Also, I have **virtualgl-libs-ia32:i386** installed - I'm not sure what it is - should I remove it or do I need it?

---

### Post by MAFoElffen on 2013-02-20
LOL --> You might want to read this:
[Why Broadcom 802.11 Linux STA driver sucks, and how to fix it]("http://pof.eslack.org/2012/05/23/why-broadcom-80211-linux-sta-driver-sucks-and-how-to-fix-it/")

---

### Post by robawalsh on 2013-02-20
> **MAFoElffen said:**
> LOL --> You might want to read this:
[Why Broadcom 802.11 Linux STA driver sucks, and how to fix it]("http://pof.eslack.org/2012/05/23/why-broadcom-80211-linux-sta-driver-sucks-and-how-to-fix-it/")

Yeah, I saw that, that didn't work. 

And any modprobe command gives me: 

FATAL: Error inserting wl (/lib/modules/3.2.0-38-generic/updates/dkms/wl.ko): Invalid argument

---

### Post by MAFoElffen on 2013-02-20
> **robawalsh said:**
> Also, I have **virtualgl-libs-ia32:i386** installed - I'm not sure what it is - should I remove it or do I need it?
Do you have wine installed? Seems that package conflicted with a lot of other packages. (Edit- I have wine installed on this 64bit box and I don't have that package installed/works fine.)

Might try to remove virtualgl-libs-ia32:i386, to try to install ia32-libs again... Then add it back in(? reaching/guess on that) or try:
```

sudo dpkg --add-architecture i386

```
which was a launchpad fix for that when this same exact thing happened about six months ago... when this last happened... when Precise was still in the dev testing cycle.

EDT-- I also see virtualgl-libs-ia32:i386 as a depends on bumblebee multi-GPU switching support.

---

### Post by robawalsh on 2013-02-20
> **MAFoElffen said:**
> Do you have wine installed? Seems that package conflicted with a lot of other packages. 

Might try to remove virtualgl-libs-ia32, to try to install ia32-libs again... Then add it back in(? reaching/guess on that) or try:
```

sudo dpkg --add-architecture i386

```which was a launchpad fix for that when this same exact thing happened about six months ago... when this last happened... when Precise was still in the dev testing cycle.

I removed virtualgl-libs-ia32 and tried to install  ia32-libs again and got the same error..

And the second suggestion: 
```

robawalsh@Dell-Inspiron-N5110:~$ sudo dpkg --add-architecture i386
[sudo] password for robawalsh: 
dpkg: error: unknown option --add-architecture
```
The command is wrong?

---

### Post by MAFoElffen on 2013-02-20
Sorry, method for adding an architecture changed with release versions:
```

Sudo echo "foreign-architecture i386" > /etc/dpkg/dpkg.cfg.d/architectures

```
Confirmed that that is how mine is setup.

---

### Post by robawalsh on 2013-02-21
> **MAFoElffen said:**
> Sorry, method for adding an architecture changed with release versions:
```

Sudo echo "foreign-architecture i386" > /etc/dpkg/dpkg.cfg.d/architectures

```Confirmed that that is how mine is setup.

 **/etc/dpkg/dpkg.cfg.d/architectures** didn't exist, so it looks like it created it, but 
 **/etc/dpkg/dpkg.cfg.d/multiarch **did exist, containing the single line:  [I]foreign-architecture i386

[/I]**sudo modprobe wl **[I]is still giving: 
[/I]
```
robawalsh@Dell-Inspiron-N5110:~$ sudo modprobe wl
[sudo] password for robawalsh: 
FATAL: Error inserting wl (/lib/modules/3.2.0-38-generic/updates/dkms/wl.ko): Invalid argument
```Trying to compile a driver is still giving me the error(s): 

```
/home/robawalsh/git/linux-next/drivers/net/wireless/brcm80211/brcmfmac/wl_cfg80211.c:4201:2: warning: statement with no effect [-Wunused-value]
cc1: some warnings being treated as errors
make[3]: *** [/home/robawalsh/git/linux-next/drivers/net/wireless/brcm80211/brcmfmac/wl_cfg80211.o] Error 1
make[2]: *** [/home/robawalsh/git/linux-next/drivers/net/wireless/brcm80211/brcmfmac] Error 2
make[1]: *** [_module_/home/robawalsh/git/linux-next/drivers/net/wireless/brcm80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-38-generic'
make: *** [default] Error 2
```What do I do next?

---

### Post by robawalsh on 2013-02-21
I don't know how relevant this is, but I tried this and got an error: 

```
robawalsh@Dell-Inspiron-N5110:/usr/src/linux-headers-3.2.0-38-generic$ sudo make oldconfig && make prepare
[sudo] password for robawalsh: 
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf --oldconfig Kconfig
#
# configuration written to .config
#
scripts/kconfig/conf --silentoldconfig Kconfig

*** Error during update of the configuration.

make[2]: *** [silentoldconfig] Error 1
make[1]: *** [silentoldconfig] Error 2
make[1]: *** No rule to make target `arch/x86/tools/relocs.c', needed by `arch/x86/tools/relocs'. Stop.
make: *** [archscripts] Error 2
robawalsh@Dell-Inspiron-N5110:/usr/src/linux-headers-3.2.0-38-generic$ 

```

---

### Post by MAFoElffen on 2013-02-21
Wait one... What? 

I just went to Broadcom to read their readme notes on the latest driver and it is precompiled and has make/build instructions for Ubuntu... which is a lot different from what you are trying:
[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

I'm trying to figure out what is wrong with that picture...

---

### Post by robawalsh on 2013-02-21
> **MAFoElffen said:**
> Wait one... What? 

I just went to Broadcom to read their readme notes on the latest driver and it is precompiled and has make/build instructions for Ubuntu... which is a lot different from what you are trying:
[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

I'm trying to figure out what is wrong with that picture...

I got the wireless driver working, along with the modprobe issue. There was something wrong with my kernel, I booted into a few versions earlier and reinstalled the 3.2.0-38 kernel, and then the wireless worked (wl module, all others blacklisted). 

But I still have the issue with building/compiling anything: 

```
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-38-generic
```Trying to reinstall it gives: 

```
Reinstallation of linux-headers-3.2.0-38-generic is not possible, it cannot be downloaded.
```(I am definitely connected to the internet...)

---

### Post by MAFoElffen on 2013-02-22
Yes, kernel. I was sort of suspecting that when you couldn't install ia32-libs...

On compiling, what commands are you using? I notice /usr... when it should be /libs...
> On Ubuntu, you will need headers and tools.  Try these commands:
# apt-get install build-essential linux-headers-generic
# apt-get build-dep linux

To check to see if you have this directory do this:

# ls /lib/modules/`uname -r`/build

BUILD INSTRUCTIONS
------------------
1. Setup the directory by untarring the proper tarball:

For 32 bit: 	hybrid-portsrc.tar.gz
For 64 bit: 	hybrid-portsrc-x86_64.tar.gz

Example:
# mkdir hybrid_wl
# cd hybrid_wl
# tar xzf <path>/hybrid-portsrc.tar or <path>/hybrid-portsrc-x86_64.tar.gz

2. Build the driver as a Linux loadable kernel module (LKM):

# make clean   (optional)
# make


This is while you are in that ~/hybrid_wl directory. Otherwise it would be 
```

make -C ~/hybrid_wl M='pwd' 

```
The above broadcom instructions are dated and fail on at least one point. You can not longer link 'uname -r' in a command set with current versions of Ubuntu. Currently, you have to manually do "uname -r" and wait for it to return it's results. Then you have to manually substitute those results back from that into your commands.

In your first post, you used:
```

make -C /lib/modules/`uname -r`/build M=`pwd` 

```
Which would have probably worked if you used 
```

make -C /lib/modules/3.2.0-38-generic/build M='pwd'

```
...instead...

But immaterial of that, if you don't have a good header file for the kernel you are running... Yes, big problems. Not just for manually compiling, but also for installing and upgrading .deb packages. I see that as a major problem, if true.

That header file is the same version kernel as you are currently running right? That is sort of cryptic saying it cannot "re-install" it, implying it is already installed or locked. If it was installed, you would think that the error would be something along the lines of "already to current version." 

Is it already installed but messed up or is it truly missing? Can you manually completely remove/apply, then install/apply it from Synaptic?

---

### Post by robawalsh on 2013-02-23
> **MAFoElffen said:**
> Yes, kernel. I was sort of suspecting that when you couldn't install ia32-libs...

On compiling, what commands are you using? I notice /usr... when it should be /libs...


This is while you are in that ~/hybrid_wl directory. Otherwise it would be 
```

make -C ~/hybrid_wl M='pwd' 

```The above broadcom instructions are dated and fail on at least one point. You can not longer link 'uname -r' in a command set with current versions of Ubuntu. Currently, you have to manually do "uname -r" and wait for it to return it's results. Then you have to manually substitute those results back from that into your commands.

In your first post, you used:
```

make -C /lib/modules/`uname -r`/build M=`pwd` 

```Which would have probably worked if you used 
```

make -C /lib/modules/3.2.0-38-generic/build M='pwd'

```...instead...

But immaterial of that, if you don't have a good header file for the kernel you are running... Yes, big problems. Not just for manually compiling, but also for installing and upgrading .deb packages. I see that as a major problem, if true.

That header file is the same version kernel as you are currently running right? That is sort of cryptic saying it cannot "re-install" it, implying it is already installed or locked. If it was installed, you would think that the error would be something along the lines of "already to current version." 

Is it already installed but messed up or is it truly missing? Can you manually completely remove/apply, then install/apply it from Synaptic?

> **chili555 said:**
> What a stubborn little problem! I wonder if it  is a locale issue; that is, if it isn't available on the Ubuntu servers  selected in Software Sources. Please see attached. I suggest you try the  USA servers and then run:```
sudo apt-get update
sudo apt-get install --reinstall linux-headers-`uname -r`
```

This seems to have worked - I switched the server by selecting "Other"  and then "Choose best server". The headers seemed to reinstall: 
```

robawalsh@Dell-Inspiron-N5110:~$ sudo apt-get update
[sudo] password for robawalsh: 
Ign http://mirror.sov.uk.goscomb.net precise InRelease
Ign http://mirror.sov.uk.goscomb.net precise-updates InRelease                 
Ign http://mirror.sov.uk.goscomb.net precise-security InRelease                
Hit http://repository.spotify.com stable InRelease                             
Get:1 http://mirror.sov.uk.goscomb.net precise Release.gpg [198 B]             
Ign http://archive.canonical.com precise InRelease                             
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://dl.google.com stable InRelease                                      
Get:2 http://mirror.sov.uk.goscomb.net precise-updates Release.gpg [198 B]     
Ign http://dl.google.com stable InRelease                                      
Ign http://dl.google.com stable InRelease                                      
Get:3 http://mirror.sov.uk.goscomb.net precise-security Release.gpg [198 B]    
Get:4 http://mirror.sov.uk.goscomb.net precise Release [49.6 kB]               
Hit http://archive.canonical.com precise Release.gpg                           
Get:5 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://dl.google.com stable Release.gpg                                    
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://archive.canonical.com precise Release                               
Hit http://extras.ubuntu.com precise Release                                   
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:6 http://mirror.sov.uk.goscomb.net precise-updates Release [49.6 kB]       
Hit http://repository.spotify.com stable/non-free amd64 Packages               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Ign http://deb.opera.com stable InRelease                                      
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://deb.torproject.org precise InRelease                                
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://repository.spotify.com stable/non-free i386 Packages                
Ign http://repository.spotify.com stable/non-free TranslationIndex             
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Get:7 http://mirror.sov.uk.goscomb.net precise-security Release [49.6 kB]      
Hit http://ppa.launchpad.net precise Release                                   
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise/main Sources                              
Get:8 http://mirror.sov.uk.goscomb.net precise/main Sources [934 kB]           
Hit http://deb.opera.com stable Release.gpg                                    
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://deb.torproject.org precise/main Sources                             
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://deb.opera.com stable Release                                        
Hit http://deb.torproject.org precise/main amd64 Packages                      
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://deb.torproject.org precise/main i386 Packages                       
Ign http://deb.torproject.org precise/main TranslationIndex                    
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://deb.opera.com stable/non-free amd64 Packages                        
Ign http://repository.spotify.com stable/non-free Translation-en_GB            
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Ign http://repository.spotify.com stable/non-free Translation-en               
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://deb.opera.com stable/non-free i386 Packages                         
Ign http://deb.opera.com stable/non-free TranslationIndex                      
Ign http://linux.dropbox.com precise InRelease                                 
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Ign http://archive.canonical.com precise/partner Translation-en_GB             
Ign http://extras.ubuntu.com precise/main Translation-en_GB                    
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://archive.canonical.com precise/partner Translation-en                
Get:9 http://mirror.sov.uk.goscomb.net precise/restricted Sources [5,470 B]    
Get:10 http://mirror.sov.uk.goscomb.net precise/universe Sources [5,019 kB]    
Hit http://ppa.launchpad.net precise/main Sources                              
Get:11 http://linux.dropbox.com precise Release.gpg [489 B]                    
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:12 http://linux.dropbox.com precise Release [2,603 B]                      
Ign http://deb.torproject.org precise/main Translation-en_GB                   
Ign http://deb.torproject.org precise/main Translation-en                      
Get:13 http://linux.dropbox.com precise/main amd64 Packages [1,148 B]          
Ign http://deb.opera.com stable/non-free Translation-en_GB                     
Ign http://deb.opera.com stable/non-free Translation-en                        
Get:14 http://linux.dropbox.com precise/main i386 Packages [1,148 B]           
Ign http://linux.dropbox.com precise/main TranslationIndex                     
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:15 http://mirror.sov.uk.goscomb.net precise/multiverse Sources [155 kB]    
Get:16 http://mirror.sov.uk.goscomb.net precise/main amd64 Packages [1,273 kB] 
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Hit http://dl.google.com stable Release.gpg                                    
Get:17 http://mirror.sov.uk.goscomb.net precise/restricted amd64 Packages [8,452 B]
Get:18 http://mirror.sov.uk.goscomb.net precise/universe amd64 Packages [4,786 kB]
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Hit http://dl.google.com stable Release.gpg                                    
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Hit http://dl.google.com stable Release                                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Hit http://dl.google.com stable Release                                        
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Hit http://dl.google.com stable Release                                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://linux.dropbox.com precise/main Translation-en_GB                    
Get:19 http://mirror.sov.uk.goscomb.net precise/multiverse amd64 Packages [119 kB]
Get:20 http://mirror.sov.uk.goscomb.net precise/main i386 Packages [1,274 kB]  
Ign http://linux.dropbox.com precise/main Translation-en                       
Get:21 http://mirror.sov.uk.goscomb.net precise/restricted i386 Packages [8,431 B]
Get:22 http://mirror.sov.uk.goscomb.net precise/universe i386 Packages [4,796 kB]
Get:23 http://mirror.sov.uk.goscomb.net precise/multiverse i386 Packages [121 kB]
Get:24 http://mirror.sov.uk.goscomb.net precise/main TranslationIndex [3,706 B]
Get:25 http://mirror.sov.uk.goscomb.net precise/multiverse TranslationIndex [2,676 B]
Get:26 http://mirror.sov.uk.goscomb.net precise/restricted TranslationIndex [2,596 B]
Get:27 http://mirror.sov.uk.goscomb.net precise/universe TranslationIndex [2,922 B]
Get:28 http://mirror.sov.uk.goscomb.net precise-updates/main Sources [367 kB]  
Get:29 http://mirror.sov.uk.goscomb.net precise-updates/restricted Sources [5,135 B]
Get:30 http://mirror.sov.uk.goscomb.net precise-updates/universe Sources [79.2 kB]
Get:31 http://mirror.sov.uk.goscomb.net precise-updates/multiverse Sources [4,725 B]
Get:32 http://mirror.sov.uk.goscomb.net precise-updates/main amd64 Packages [582 kB]
Get:33 http://mirror.sov.uk.goscomb.net precise-updates/restricted amd64 Packages [9,565 B]
Get:34 http://mirror.sov.uk.goscomb.net precise-updates/universe amd64 Packages [182 kB]
Get:35 http://mirror.sov.uk.goscomb.net precise-updates/multiverse amd64 Packages [9,421 B]
Get:36 http://mirror.sov.uk.goscomb.net precise-updates/main i386 Packages [593 kB]
Get:37 http://mirror.sov.uk.goscomb.net precise-updates/restricted i386 Packages [9,503 B]
Get:38 http://mirror.sov.uk.goscomb.net precise-updates/universe i386 Packages [184 kB]
Get:39 http://mirror.sov.uk.goscomb.net precise-updates/multiverse i386 Packages [10.4 kB]
Get:40 http://mirror.sov.uk.goscomb.net precise-updates/main TranslationIndex [3,564 B]
Get:41 http://mirror.sov.uk.goscomb.net precise-updates/multiverse TranslationIndex [2,605 B]
Get:42 http://mirror.sov.uk.goscomb.net precise-updates/restricted TranslationIndex [2,461 B]
Get:43 http://mirror.sov.uk.goscomb.net precise-updates/universe TranslationIndex [2,850 B]
Get:44 http://mirror.sov.uk.goscomb.net precise-security/main Sources [63.1 kB]
Get:45 http://mirror.sov.uk.goscomb.net precise-security/restricted Sources [1,950 B]
Get:46 http://mirror.sov.uk.goscomb.net precise-security/universe Sources [22.2 kB]
Get:47 http://mirror.sov.uk.goscomb.net precise-security/multiverse Sources [1,382 B]
Get:48 http://mirror.sov.uk.goscomb.net precise-security/main amd64 Packages [228 kB]
Get:49 http://mirror.sov.uk.goscomb.net precise-security/restricted amd64 Packages [3,969 B]
Get:50 http://mirror.sov.uk.goscomb.net precise-security/universe amd64 Packages [68.2 kB]
Get:51 http://mirror.sov.uk.goscomb.net precise-security/multiverse amd64 Packages [2,193 B]
Get:52 http://mirror.sov.uk.goscomb.net precise-security/main i386 Packages [237 kB]
Get:53 http://mirror.sov.uk.goscomb.net precise-security/restricted i386 Packages [3,968 B]
Get:54 http://mirror.sov.uk.goscomb.net precise-security/universe i386 Packages [69.9 kB]
Get:55 http://mirror.sov.uk.goscomb.net precise-security/multiverse i386 Packages [2,368 B]
Get:56 http://mirror.sov.uk.goscomb.net precise-security/main TranslationIndex [74 B]
Get:57 http://mirror.sov.uk.goscomb.net precise-security/multiverse TranslationIndex [71 B]
Get:58 http://mirror.sov.uk.goscomb.net precise-security/restricted TranslationIndex [71 B]
Get:59 http://mirror.sov.uk.goscomb.net precise-security/universe TranslationIndex [73 B]
Get:60 http://mirror.sov.uk.goscomb.net precise/main Translation-en_GB [96.4 kB]                 
Get:61 http://mirror.sov.uk.goscomb.net precise/main Translation-en [726 kB]                      
Get:62 http://mirror.sov.uk.goscomb.net precise/multiverse Translation-en_GB [79.8 kB]            
Get:63 http://mirror.sov.uk.goscomb.net precise/multiverse Translation-en [93.4 kB]               
Get:64 http://mirror.sov.uk.goscomb.net precise/restricted Translation-en_GB [2,406 B]            
Get:65 http://mirror.sov.uk.goscomb.net precise/restricted Translation-en [2,395 B]               
Get:66 http://mirror.sov.uk.goscomb.net precise/universe Translation-en_GB [5,492 B]              
Get:67 http://mirror.sov.uk.goscomb.net precise/universe Translation-en [3,341 kB]                
Get:68 http://mirror.sov.uk.goscomb.net precise-updates/main Translation-en_GB [96.4 kB]          
Get:69 http://mirror.sov.uk.goscomb.net precise-updates/main Translation-en [260 kB]              
Get:70 http://mirror.sov.uk.goscomb.net precise-updates/multiverse Translation-en_GB [79.8 kB]    
Get:71 http://mirror.sov.uk.goscomb.net precise-updates/multiverse Translation-en [5,694 B]       
Get:72 http://mirror.sov.uk.goscomb.net precise-updates/restricted Translation-en_GB [2,406 B]    
Get:73 http://mirror.sov.uk.goscomb.net precise-updates/restricted Translation-en [2,328 B]       
Get:74 http://mirror.sov.uk.goscomb.net precise-updates/universe Translation-en_GB [5,492 B]      
Get:75 http://mirror.sov.uk.goscomb.net precise-updates/universe Translation-en [108 kB]          
Get:76 http://mirror.sov.uk.goscomb.net precise-security/main Translation-en [111 kB]             
Get:77 http://mirror.sov.uk.goscomb.net precise-security/multiverse Translation-en [995 B]        
Get:78 http://mirror.sov.uk.goscomb.net precise-security/restricted Translation-en [978 B]        
Get:79 http://mirror.sov.uk.goscomb.net precise-security/universe Translation-en [43.2 kB]        
Hit http://dl.google.com stable/main amd64 Packages                                               
Hit http://dl.google.com stable/main i386 Packages
Ign http://dl.google.com stable/main TranslationIndex
Hit http://dl.google.com stable/main amd64 Packages
Hit http://dl.google.com stable/main i386 Packages
Ign http://dl.google.com stable/main TranslationIndex
Hit http://dl.google.com stable/main amd64 Packages
Hit http://dl.google.com stable/main i386 Packages
Ign http://dl.google.com stable/main TranslationIndex
Ign http://dl.google.com stable/main Translation-en_GB
Ign http://dl.google.com stable/main Translation-en
Ign http://dl.google.com stable/main Translation-en_GB
Ign http://dl.google.com stable/main Translation-en
Ign http://dl.google.com stable/main Translation-en_GB
Ign http://dl.google.com stable/main Translation-en
Fetched 26.5 MB in 2min 11s (202 kB/s)
Reading package lists... Done
robawalsh@Dell-Inspiron-N5110:~$ sudo apt-get install --reinstall linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 985 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://mirror.sov.uk.goscomb.net/ubuntu/ precise-updates/main linux-headers-3.2.0-38-generic amd64 3.2.0-38.61 [985 kB]
Fetched 985 kB in 0s (2,381 kB/s)                  
(Reading database ... 604258 files and directories currently installed.)
Preparing to replace linux-headers-3.2.0-38-generic 3.2.0-38.61 (using  .../linux-headers-3.2.0-38-generic_3.2.0-38.61_amd64.deb) ...
Unpacking replacement linux-headers-3.2.0-38-generic ...
Setting up linux-headers-3.2.0-38-generic (3.2.0-38.61) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-38-generic /boot/vmlinuz-3.2.0-38-generic
Error! Bad return status for module build on kernel: 3.2.0-38-generic (x86_64)
Consult /var/lib/dkms/psmouse-alps/0.10/build/make.log for more information.
robawalsh@Dell-Inspiron-N5110:~$ 
```Apart from the ```
Error! Bad  return status for module build on kernel: 3.2.0-38-generic (x86_64)
Consult /var/lib/dkms/psmouse-alps/0.10/build/make.log for more  information.
```I would delete this if I knew how (I now have version  0.4), but I don't think this is the problem. 

But anyway, the headers looked reinstalled, and I tried compiling a  package from source to test (nautilus-dropbox-1.4.0) and this seemed  successful. 

Maybe the errors compiling the wireless drivers were more to do with  something wrong with the commands used to build the drivers for my  system

Thanks for help

---

