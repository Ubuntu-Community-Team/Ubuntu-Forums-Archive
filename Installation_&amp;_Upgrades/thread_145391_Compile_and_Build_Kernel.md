---
title: "Compile and Build Kernel"
date: 2006-03-16
forum: Installation &amp; Upgrades
---

### Post by JeromeDuke on 2006-03-16
Hi,

I have installed Ubuntu 2.6.12.-9-386 on a laptop and want to configure it to work with my Linksys wireless card.

Following the instructions here: 
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

It tells me I need to have "compiled and built the kernel before".

So to do that, I'm following the instructions here:
[http://www.ubuntuforums.org/showthread.php?t=24853](http://www.ubuntuforums.org/showthread.php?t=24853)

I am logged in as root. When I run the line:
sudo apt-get install build-essential linux-source-2.6 libncurses5-dev kernel-package

It tells me "E: Couldn't find package linux=source-2.6"

So I guessed I needed to change it to 2.6.12 which I did, and now I get the message:

build-essential is already the newest version
Package linux-source-2.6.12 is not available, but is referenced by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package linux-source-2.6.12 has no installation candidate

Any ideas how I should do it ? (Also, do I really need to compile and build the kernel to get the wireless card working ? I've read a lot of posts about how this is not really necessary nowadays.)

Thanks.

---

### Post by Heliix on 2006-03-16
hi Jerome
there is an excellent howto
[http://www.ubuntuforums.org/showthread.php?t=43065](http://www.ubuntuforums.org/showthread.php?t=43065)
i´d only suggest to use the latest 2.6.15 kernel instead of 2.6.12 (look at [http://www.kernel.org](http://www.kernel.org))
whether you really need to compile your kernel? maybe not, accordings to my experiences, if you just install ubuntu with the default 2.6.12 kernel it has already built-in support for *nearly everything* that *may be useful to someone*
look at the /boot/config file to see whether your kernel already supports wifi

good luck! :-)

---

### Post by JeromeDuke on 2006-03-16
Hi,

I followed that link and am following the directions, when I get to "sudo apt-get install kernel-package"

It says "E: Couldn't find package kernel-package"

Am I supposed to substitute anything for "kernel-package" ?

Similarly, it couldn't find libncurses5-dev and libqt3-mt-dev

Also, I looked at the /boot/config file - what am I looking for to see if it already supports wireless ? I've done the obvious searches.

All of the articles about my linksys wireless card suggest I have to install ndiswrapper, so I think I am going to have to pursue the build and compile of the kernel.

Thanks.

---

### Post by Heliix on 2006-03-17
hmm, sounds strange..
you can download the latest kernel at [www.kernel.org](www.kernel.org) and extract the archive to /usr/src directory and create the symbolic link to this kernel directory (as described in the howto ;-) )
couldn´t find libncurses5-dev and libqt3-mt-dev?
check your /etc/apt/sources.list (maybe you´ll need to include additional web sites), try apt-cache search libncurses (*or libqt) to find similar packages-but it´s weird because i had no problems at all with apt-getting these packages a month before or so
you can as well find the desired packages somewhere on net and install them from source
and what should be included in kernel to support wireless? i have no experiences with wifi at all, but.. find out what type of wifi card you have, what does it need to work and go through the section networking, obsolete wireless card support.. in my default kernel configuration (2.6.12-10, after installing breezy from cd), there is supported *almost everything* as a module (may be enough to get it work, or-may not..)
so i´d just try it first with the "old" kernel
Heliix

---

### Post by hfern on 2006-03-17
I seem to have the same experience: I installed Breezy 2 weeks ago from a freshly download iso image. The installed kernel is 2.6.12-9-386. When I do a "apt-get install kernel-source", I get: 

Reading package lists... Done
Building dependency tree... Done
Package kernel-source is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package kernel-source has no installation candidate

Do I do something wrong or is 2.6.12 already obsolete. I do want a 2.6 kernel, but am not too worried about the last digit. Is there a way how to get a complete Ubuntu distribution, complete with kernel sources? Thanks.

---

### Post by Heliix on 2006-03-19
when i do "apt-get install kernel-source", i got a list of virtual kernel packages (2.6.10 being the newest :-/)
i'd suggest to download the latest kernel from the kernel web site
i guess a complete ubuntu distro already has "complete kernel sources" 
in /usr/src/linux directory perhaps (did you try the kernel compilation from this place?)
but i'm not sure as my installation wasn't quite standard
is it such a problem for you to get the kernel sources from the web?

---

### Post by az on 2006-03-19
1.  The package is called linux-source.
2.  YOU DO NOT NEED TO RECOMPILE THE KERNEL!

Ndiswrapper is already included.  Just install the userspace tool to use it

ndiswrapper-utils.


You should be good to go from there.

If you do need to compile a kernel module, use the linux-headers package for your current linux-image.  That way, you can add modules to the same kernel that is running without having to recompile everything.  You do not need to do this for ndiswrapper, though, since the module is already there.

---

