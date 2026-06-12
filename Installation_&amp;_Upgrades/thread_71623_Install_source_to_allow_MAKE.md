---
title: "Install source to allow MAKE?"
date: 2005-10-03
forum: Installation &amp; Upgrades
---

### Post by spdiscus on 2005-10-03
Howdy. I'm trying to just get an install right before I try to get everything working correctly with the entire OS.
I know I need the madwifi drivers to get my atheros card (Di-Link G630 C.2) to work, but I don't even know where to start. 
The laptop I'm using has zero internet connectivity, so I'm forced to work on two computers. I downloaded the madwifi tar, but I'm not sure what to do with it.
After "tar -xvvzf madwifi-cvs-current.tar.gz", it looks like everything is unzipped and placed in a directory on my desktop.
Navigating to the madwifi directory and typing "make", I get...
"Makefile.inc:94: *** KERNELPATH must be defined. Stop."
If I need source files, how do I install them (I have the source disc 1 iso). If I need to define the kernelpath, how would i do that?
This is probably vague, but it is 'frist psot' and all, so I'm willing to provide any information necessary...just ask for it.
Thanks in advance. I'd love to wipe all XP leftovers from memory, but I'm going to need a bit of help.
And if there's already a thread/forum/discussion/tutorial addressing this problem, I'm fine reading it. I just haven't been able to find it.

[EDIT]
Most suggestion posts say to use apt-get to install/fix everything. Like I said above, I don't have access to any internet connection on the install machine, so apt-get won't work for me...I think. If I'm wrong, feel free to yell at me. :D

---

### Post by darkmatter on 2005-10-04
Post the  contents of that Makefile so I can take a look at it.

---

### Post by spdiscus on 2005-10-04
Steps so far: 
Install (standard) Ubuntu 5.04 from the base install disc.
Separate machine - download madwifi and burn to disc.
Copy madwifi-cvs-current.tar.gz to Desktop.
Navigate to /home/me/Desktop/"
"tar -xvvzf madwifi-cvs-current.tar.gz" - I wasn't sure where exactly to extract
"cd madwifi"
"make"
--Makefile.inc:94: ***KERNELPATH must be defined. Stop.

I'm assuming that I may need the kernel source, but I'm not sure how that is installed/copied over. I have the source isos, but that doesn't mean I know what to do with them.

Here's the contents of /home/me/Desktop/madwifi/Makefile:
#
# Copyright (c) 2002-2005 Sam Leffler, Errno Consulting
# All rights reserved.
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions
# are met:
# 1. Redistributions of source code must retain the above copyright
#    notice, this list of conditions and the following disclaimer,
#    without modification.
# 2. Redistributions in binary form must reproduce at minimum a disclaimer
#    similar to the "NO WARRANTY" disclaimer below ("Disclaimer") and any
#    redistribution must be conditioned upon including a substantially
#    similar Disclaimer requirement for further binary redistribution.
# 3. Neither the names of the above-listed copyright holders nor the names
#    of any contributors may be used to endorse or promote products derived
#    from this software without specific prior written permission.
#
# Alternatively, this software may be distributed under the terms of the
# GNU General Public License ("GPL") version 2 as published by the Free
# Software Foundation.
#
# NO WARRANTY
# THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
# ``AS IS'' AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
# LIMITED TO, THE IMPLIED WARRANTIES OF NONINFRINGEMENT, MERCHANTIBILITY
# AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL
# THE COPYRIGHT HOLDERS OR CONTRIBUTORS BE LIABLE FOR SPECIAL, EXEMPLARY,
# OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF
# SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS
# INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER
# IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE)
# ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF
# THE POSSIBILITY OF SUCH DAMAGES.
#
# $Id: Makefile.inc,v 1.39 2005/07/13 07:56:22 br1 Exp $
#

ifeq ($(obj),)
obj=	.
endif

# other locales sometimes cause trouble
export LC_ALL = POSIX

# OS is the target operating system. Currently only Linux is supported.
OS=		linux

# TARGET defines the target platform ISA per GNU rules.
# It must match one of the target platforms supported by
# the HAL.  To see the set of target platforms look at
# hal/linux/*.inc.  You can set this in the environment
# to override the default setting.
#
ifeq ($(TARGET),)
TARGET=		i386-elf
endif

# BUS defines the bus type to which the wireless devices is attached.
# Currently, the valid BUS types are PCI and AHB.  If BUS is not
# defined, then, we assume the bus type is PCI
ifndef BUS
BUS=		PCI
endif

# DESTDIR is used as path prefix during installation.
DESTDIR ?=

# KERNELPATH is the path to the target kernel's build/source area.
# This is used to obtain the kernel configuration and include files.
# If automatic determination doesn't work as desired, you have to
# manually set it, for example with:
# make KERNELPATH=/path/to/kernel/source

# TOOLPATH is the path which contains the crosscompile toolchain (?)

ifeq ($(strip ${BUS}),AHB)
# Bus type AHB forces the target platform to be mipsisa32.
TARGET :=	mipsisa32-be-elf

# Bus type AHB requires KERNELPATH and TOOLPATH to be set manually.
ifndef KERNELPATH
$(error KERNELPATH must be defined for bus type AHB.)
endif
ifndef TOOLPATH
$(error TOOLPATH must be defined for bus type AHB.)
endif

else

KERNELPATH ?= $(firstword $(wildcard $(DESTDIR)/lib/modules/$(shell uname -r)/build /usr/src/linux))

ifeq ($(KERNELPATH),)
$(error KERNELPATH must be defined)
endif

endif

# sanity check: does KERNELPATH exist?
ifeq ($(wildcard $(KERNELPATH)),)
$(error KERNELPATH: $(KERNELPATH) does not exist)
endif

# KERNELRELEASE is the target kernel's version.  If KERNELRELEASE
# is not set in the environment then it is taken from the running
# system.
# To determine the correct version a mini-Makefile is piped to make
# which includes the Makefile in KERNELPATH and prints out the version.
# This is done to come by problems recently introduced with some distros
# and newer kernel releases.
#
# Note: '\044' used instead of '$' in order to avoid make complaining like
# "Recursive variable `KERNELRELEASE' references itself (eventually)."
KERNELRELEASE ?= $(shell echo -e 'madwifi_$$_`date +%s`:\n\t@echo \044(KERNELRELEASE)\ninclude Makefile' | make -C $(KERNELPATH) -s -f-)

# KERNELCONF is the name of the file that holds the configuration
# of the target kernel.
KERNELCONF ?=	${KERNELPATH}/.config

# sanity check: does KERNELCONF exist?
ifeq ($(wildcard $(KERNELCONF)),)
$(error KERNELCONF: $(KERNELCONF) does not exist.)
endif

# SYSTEMMAP is the name of the System.map file for the target
# kernel. This will be needed when DESTDIR is defined in order
# to run depmod properly.
SYSTEMMAP ?= 	${KERNELPATH}/System.map

# MODULEPATH nominates the directory where the modules will be
# installed to
ifeq ($(strip ${BUS}),AHB)
MODULEPATH := 	${KERNELPATH}/arch/mips/ar531x/RAMDISK/rootdir/lib/modules/${KERNELRELEASE}/net
else
MODULEPATH ?=	/lib/modules/${KERNELRELEASE}/net
endif

# WIRELESSEXT contains information about the version of the wireless
# extensions that are available in the target kernel
WIRELESSEXT ?=	$(shell cat $(KERNELPATH)/include/linux/wireless.h | grep "\#define WIRELESS_EXT" | cut -f2)

# Some settings that depend on actual kernel release
ifneq ($(findstring 2.6,$(KERNELRELEASE)),)
export-objs	:=
list-multi	:=
KMODSUF		:= ko
else
KMODSUF		:= o
endif

NM=            nm
AWK=           awk

#
# Path to the HAL source code.
#
ifeq ($(HAL),)
HAL=	${obj}/${DEPTH}/hal
endif
#
# Path to the HAL build area.
#
ATH_HAL=${DEPTH}/ath_hal
#
# Path to the 802.11 include files.
#
WLAN=	${DEPTH}/net80211
#
# Path to the Atheros device driver.
#
ATH=	${DEPTH}/ath
#
# Path to the rate control algorithm.
#
#ATH_RATE=$(shell find ath_rate/ -maxdepth 1 ! -name CVS ! -name ath_rate/ -type d)
ifeq ($(ATH_RATE),)
ATH_RATE=ath_rate/sample
endif

INCS=	-include ${obj}/${DEPTH}/include/compat.h -I${obj}/${DEPTH}/include

ifeq ($(strip ${BUS}),AHB)
INCS+= -isystem ${TOOLPATH}/include
endif

include ${HAL}/public/${TARGET}.inc

SYMBOLSDIR=${DEPTH}/symbols

---

### Post by darkmatter on 2005-10-04
You can grab the sources for your kernel from Synaptic.

After you do that, run make again as below
```
make KERNELPATH=/path/to/kernel/source
```
if a standard make still does not autodetect the sources.

---

### Post by spdiscus on 2005-10-05
I'm not sure how to do that. I added all four source CD-ROMs to Synaptic (Synaptic Package Manager > Edit > Add CD-ROM), and I also did "apt-cdrom add" for all four discs. 
I can't find a relevent package in Synaptic, searching for "linux," "source," or "kernel."
And "sudo apt-get install linux-source-2.6.10" didn't find the package.

Do you know of a basic step I'm missing? Again, I think my main issue is that I have the source discs, but I can't find any tutorials on what to do with them.

Thanks for the responses/tolerance so far. :)

---

### Post by spdiscus on 2005-10-05
OK, so after "sudo apt-cdrom install -a" for all four source discs, I still can't figure out how to actually apt-get the source files.
/etc/apt/sources.list shows all four CDs as "deb-src cdrom:[DISC INFO]" as well as "deb cdrom:[...]", but "sudo apt-get install linux-source-2.6.10" and "sudo apt-get install kernel-source-2.6.10" both fail because the package isn't found. 
"sudo apt-get install linux-2.6.10" prints...
"Package linux-source-2.6.10 is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package linux-source-2.6.10 has no installation candidate".

Thoughts?
With all four discs, what do I have to type to get apt to recognize the source files, or what do I have to do with Synaptic to get it to recognize the source package?

---

### Post by spdiscus on 2005-10-06
Bump and more info...

All four src CDs are listed in /etc/apt/sources.list
All four src CDs are listed in /var/lib/apt/cdroms.list
"linux-source-2.6.10" is listed in /var/lib/apt/lists/Ubuntu....dists_hoary_main_source_Sources

And the following output is kinda weird.
****
"apt-cache showpkg linux-source-2.6.10" ...

Package: linux-source-2.6.10
Versions:

Reverse Depends:
   linux-image-2.6.10-5-386, linux-source-2.6.10
Dependencies:
Provides:
Reverse Provides:
****
"apt-cache showsrc linux-source-2.6.10"

I can't cut and paste this output, and I don't feel like typing it all in, but it looks like all possible output is included (no blank spots like with showpkg), and it lists three files (.dsc, .orig.tar.gz, and .diff.gz) and the correct CD directory at the bottom (/pool/main/l/linux-source-2.6.10).

---

### Post by spdiscus on 2005-10-06
Bump again.
Anyone?
I have the source discs. I've "apt-cdrom add -a" all of them.
"apt-cache pkgnames linux" shows linux-source-2.6.10 as an available package.

I'm just a newbie trying to install source files from the source ISOs. Any ideas?

Is there such a thing as recursive dependency? 
"sudo apt-cache rdepends linux-source-2.6.10" prints "<linux-source-2.6.10>". Is it telling me it needs itself to install properly?

Do you think the "%20" replacing spaces in /var/lib/apt/lists is obstructing installation?

---

### Post by az on 2005-10-06
You need build-essential andd the linux-headers to build kernel modules.  

Install linux-headers-2.6.10-5-386 (or 686 or k7, depending on what you run)

---

### Post by spdiscus on 2005-10-06
Thanks for the response.

"sudo apt-get install linux-headers-2.6.10-5-386" - couldn't find package
"sudo apt-get install linux-headers-2.6.10" - couldn't find package
same with kernel-headers

---

### Post by spdiscus on 2005-10-06
Is there just a way for me to have it install directly from the CD? I know the file path - /media/cdrom0/pool/main/l/linux-source-2.6.10
I must be missing something really basic; I just don't know what.

---

### Post by darkmatter on 2005-10-06
Sorry for the late reply, I was having trouble finding a solution.

In regard to your last post, you can just copy the .deb to directory on your drive. Then cd to that directory, and install with
```
sudo dpkg -i <package name>.deb
```

assuming the source package on the CD is a .deb

---

### Post by spdiscus on 2005-10-06
The three files in the directory are linux-source-2.6.10...
...-34.diff.gz
..._2.6.10-34.dsc
..._2.6.10.orig.tar.gz

I ran tar -xvvzf on the .orig.tar.gz, but I don't know what to do with the folder it created. I didn't find any .deb files.

---

### Post by az on 2005-10-06
Okay, what cd are you using that has the linux-source and not the linux headers on it?

---

### Post by spdiscus on 2005-10-06
[QUOTE=azz]Okay, what cd are you using that has the linux-source and not the linux headers on it?[/QUOTE]
That's the problem. I don't think apt-get is searching the package list of things on the CDs, even though all four CDs show in sources.list. They are the only four lines not commented out in the file.
Example: deb-src cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release Source-1 (20050407)]/ hoary main restricted
My discs are the four standard ISOs from Ubuntu's one source site.

linux-kernel-headers shows as "already the newest version," but linux-source-2.6.10 still says "has no installation candidate"
Both appear with "apt-cache pkgnames linux".

Let's start from the beginning :) ...
If you had the source ISOs and no internet connection, how would you install the source?

What I tried...
"sudo apt-cdrom add -a"       for discs 1 through 4
"sudo apt-get update"          to register the new packages found on the discs
"sudo apt-get install linux-source-2.6.10"     to install from disc 2, which holds the linux-source-2.6.10 folder

I'm sure it can't be as difficult as I've ended up making it, but Google-ing anything with the word "source" throws all kinds of matches that just get in the way.

---

### Post by darkmatter on 2005-10-06
Part of the problem is that the files on the CD's are .tar.gz.

Apt handles .debs

I'm still trying to find the solution. I'll get back to you as soon as possible.

---

### Post by spdiscus on 2005-10-07
Uh, I hope it isn't this easy, but after re-reading the man pages, it looks like...

 "apt-get **source** linux-source-2.6.10" 

...is the flag that's needed to look in sources.list for deb-src lines (like my source discs).

I'll try when I get home from work and re-post.
Thanks for the help, so far!

And feel free to tell me if I'm mis-reading this...

**man apt-get**
> source
    source causes apt-get to fetch source packages. APT will examine the available packages to decide which source package to fetch. It will then find and download into the current directory the newest available version of that source package. Source packages are tracked separately from binary packages via deb-src type lines in the sources.list(5) file. This probably will mean that you will not get the same source as the package you have installed or as you could install. If the --compile options is specified then the package will be compiled to a binary .deb using dpkg-buildpackage, if --download-only is specified then the source package will not be unpacked.

    A specific source version can be retrieved by postfixing the source name with an equals and then the version to fetch, similar to the mechanism used for the package files. This enables exact matching of the source package name and version, implicitly enabling the APT::Get::Only-Source option.

    Note that source packages are not tracked like binary packages, they exist only in the current directory and are similar to downloading source tar balls. 

---

### Post by spdiscus on 2005-10-07
Update again:
apt-get source linux-source-2.6.10 correctly downloaded and unpackaged the source files.
I now have the folder /home/me/linux-source-2.6.10-2.6.10 :)

So, back to the beginning. How would I install madwifi?
I set KERNELPATH=/home/me/linux-source-2.6.10-2.6.10, but running make in the madwifi folder now tells me there's no '/home/me/linux-source-2.6.10-2.6.10//.config'

I was probably supposed to do something after it unpacked the source, but I don't know what.

---

