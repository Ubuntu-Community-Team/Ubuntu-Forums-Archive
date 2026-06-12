---
title: "Cannot get HP Laptop to Boot from Live USB - MADDENING!"
date: 2011-04-25
forum: Installation &amp; Upgrades
---

### Post by evilbellylint on 2011-04-25
Fed up with Windows and ready to become a Linux convert. Here's the only problem:

I've created no less than four separate Live USB distros - all using different USB sticks - 
yet my HP Pavilion dv7 refuses to recognize any of them as "bootable devices."

1) Have formatted USB sticks in FAT16 & FAT32 - neither made a difference.

2) Have created bootable USB sticks using Ubuntu Minimal Live install; Ubuntu full Live install; PuppyLinux Live install; even a simple gparted live install - none will boot.

3) Have checked & re-checked that BIOS is set to boot first from USB drive device.

4) 2 of the 4 USB sticks are new, fresh out of the packaging; and 3 of the 4 USB sticks are each from different manufacturers - so I'm fairly certain it's not a issue of a particular brand being incompatible, nor is it due to the sticks being corrupted somehow.

5) Each of the 4 live distros appears to have downloaded just fine - all necessary files appear to be in order.

6) Have tried using Unetbootin, Ubuntu's own live usb tool, and 1 or 2 others - all have failed to boot my HP laptop.

7) Have even tried removing all non-essential hardware before booting - even booting with no hard drives installed - system still returns the error "no bootable device detected."


This laptop is only 2 years old; I know it should be able to boot from USB. I can boot from a (rather old) SliTaz distro on CD just fine - but I need a persistent USB stick so I can easily add packages as needed, etc...

There HAS to be something basic I'm missing here. Was very enthusiastic about finally committing to Linux, but after an entire week of reading literally hundreds of forum pages and trying everything I know, I'm just about ready to go back to Windows.

Any help would be greatly appreciated at this point. I'm about out of ideas. :confused:

EBL

====================

HP Pavilion dv7-1260us
AMD64 Turion X2 
4GB RAM
ATI Radeon HD 3200 graphics

---

### Post by Dutch70 on 2011-04-25
Hi and welcome to UF

See if there is something here to help you. 
[[COLOR="RoyalBlue"]http://psychocats.net/ubuntu/usb[/COLOR]]("http://psychocats.net/ubuntu/usb")

Hopefully it will be removing the U3 software that helps, but if not maybe PLoP can help.

---

### Post by Hedgehog1 on 2011-04-25
As I just went through this with my HP dv8 laptop; this issue is not Linux in any way.

HP laptops just has an odd Bios boot behavior that, once you know, becomes a non-issue.

Insert the USB stick you want to work from, power up and then press the F9. Use the Up/Down arrows to select the USB. Press Enter.

That is the whole secret.  Took me 2 hours to find it...


***The Hedge***

:KS

---

### Post by evilbellylint on 2011-04-25
@ Hedgehog1 - I'll give that a try right now, and report back momentarily.

@ Dutch70 - thank you for the link. I had actually come across that earlier but was
uncertain how to proceed after receiving some ./config errors. If the above fix suggested
by Hedgehog1 fails to work, I will post my config.log in hopes that you or someone else
might be willing to help decipher what it is I need to do next.

cheers,

EBL

---

### Post by Hedgehog1 on 2011-04-25
Well... It has been 10 minutes... Where could he be??? :D

---

### Post by evilbellylint on 2011-04-25
hahaha...sorry. Right here!

Well, as soon as I rebooted and tapped F9 it was clear I'd already tried this option.
F9 does indeed call up the Boot Manager -- problem is only a single option is listed:

[B][COLOR=Blue]Boot Option Menu

Internal CD/DVD ROM Drive[/COLOR][/B]


I again tapped F10 to enter BIOS setup ->System Configuration->Boot Options
and the only options listed above [COLOR=Blue]**>Boot Order **[/COLOR]are:

[COLOR=Blue][B]CD-ROM Boot <Enabled>
Floppy Boot <Enabled>
Internal Network Adapter <Disabled>[/B][/COLOR]

And beneath, I have [COLOR=Blue]**>Boot Order **[/COLOR]set as follows:

[COLOR=Blue][B]Boot Order

USB Diskette on Key/USB Hard Drive
USB Floppy
Internal CD/DVD ROM Drive
USB CD/DVD Hard Drive
Notebook Hard Drive[/B][/COLOR]

In observing the "flashing light" on the USB stick, it's apparent the system is not recognizing the USB device in time for it to be listed as a boot option when tapping 
F9 to call up the Boot Manager....

---

### Post by evilbellylint on 2011-04-25
Will post the config.log from the U3 Removal Tool in a few minutes...

(as this SliTaz distro is on a CD and incapable of saving persitent changes,
I'll need to d/l the .tar again, run ./config, and post the error log...)

EBL

---

### Post by evilbellylint on 2011-04-25
(configure.log pasted at the end)

1) d/l'd u3-tool-0.3 from Sourceforge & extracted to Desktop

2) opened xterm; obtained root priveleges; cd to /home/tux/Desktop/u3-tool-0.3

3) ran ./configure and the error that jumps right out at me is: 

"[COLOR=Blue]no acceptable C compiler found in $PATH[/COLOR]"


============================================
**Here is a copy/paste of the full config.log:**
============================================

This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by u3-tool configure 0.3, which was
generated by GNU Autoconf 2.63.  Invocation command line was

  $ ./configure 

## --------- ##
## Platform. ##
## --------- ##

hostname = slitaz
uname -m = i686
uname -r = 2.6.29.3-slitaz
uname -s = Linux
uname -v = #1 SMP Mon May 25 02:01:23 CEST 2009

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = unknown
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1883: checking for a BSD-compatible install
configure:1951: result: /usr/bin/install -c
configure:1962: checking whether build environment is sane
configure:2005: result: yes
configure:2030: checking for a thread-safe mkdir -p
configure:2069: result: ./install-sh -c -d
configure:2082: checking for gawk
configure:2112: result: no
configure:2082: checking for mawk
configure:2112: result: no
configure:2082: checking for nawk
configure:2112: result: no
configure:2082: checking for awk
configure:2098: found /usr/bin/awk
configure:2109: result: awk
configure:2120: checking whether make sets $(MAKE)
configure:2146: result: no
configure:2335: checking build system type
configure:2353: result: i686-pc-linux-gnuoldld
configure:2375: checking host system type
configure:2390: result: i686-pc-linux-gnuoldld
configure:2462: checking for gcc
configure:2492: result: no
configure:2555: checking for cc
configure:2602: result: no
configure:2658: checking for cl.exe
configure:2688: result: no
configure:2712: error: in `/home/tux/Desktop/u3-tool-0.3':
configure:2715: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=i686-pc-linux-gnuoldld
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_LIBS_set=
ac_cv_env_LIBS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_host=i686-pc-linux-gnuoldld
ac_cv_path_install='/usr/bin/install -c'
ac_cv_prog_AWK=awk
ac_cv_prog_make_make_set=no

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='${SHELL} /home/tux/Desktop/u3-tool-0.3/missing --run aclocal-1.10'
AMDEPBACKSLASH=''
AMDEP_FALSE=''
AMDEP_TRUE=''
AMTAR='${SHELL} /home/tux/Desktop/u3-tool-0.3/missing --run tar'
AUTOCONF='${SHELL} /home/tux/Desktop/u3-tool-0.3/missing --run autoconf'
AUTOHEADER='${SHELL} /home/tux/Desktop/u3-tool-0.3/missing --run autoheader'
AUTOMAKE='${SHELL} /home/tux/Desktop/u3-tool-0.3/missing --run automake-1.10'
AWK='awk'
CC=''
CCDEPMODE=''
CFLAGS=''
CPP=''
CPPFLAGS=''
CYGPATH_W='echo'
DEFS=''
DEPDIR=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
EXEEXT=''
GREP=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
INSTALL_STRIP_PROGRAM='$(install_sh) -c -s'
LDFLAGS=''
LIBOBJS=''
LIBS=''
LTLIBOBJS=''
MAKEINFO='${SHELL} /home/tux/Desktop/u3-tool-0.3/missing --run makeinfo'
MKDIR_P='./install-sh -c -d'
OBJEXT=''
PACKAGE='u3-tool'
PACKAGE_BUGREPORT='daviedev@users.sourceforge.net'
PACKAGE_NAME='u3-tool'
PACKAGE_STRING='u3-tool 0.3'
PACKAGE_TARNAME='u3-tool'
PACKAGE_VERSION='0.3'
PATH_SEPARATOR=':'
SET_MAKE='MAKE=make'
SHELL='/bin/bash'
STRIP=''
VERSION='0.3'
ac_ct_CC=''
am__fastdepCC_FALSE=''
am__fastdepCC_TRUE=''
am__include=''
am__isrc=''
am__leading_dot='.'
am__quote=''
am__tar='${AMTAR} chof - "$$tardir"'
am__untar='${AMTAR} xf -'
bindir='${exec_prefix}/bin'
build='i686-pc-linux-gnuoldld'
build_alias=''
build_cpu='i686'
build_os='linux-gnuoldld'
build_vendor='pc'
datadir='${datarootdir}'
datarootdir='${prefix}/share'
docdir='${datarootdir}/doc/${PACKAGE_TARNAME}'
dvidir='${docdir}'
exec_prefix='NONE'
host='i686-pc-linux-gnuoldld'
host_alias=''
host_cpu='i686'
host_os='linux-gnuoldld'
host_vendor='pc'
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
install_sh='$(SHELL) /home/tux/Desktop/u3-tool-0.3/install-sh'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localedir='${datarootdir}/locale'
localstatedir='${prefix}/var'
mandir='${datarootdir}/man'
mkdir_p='$(top_builddir)/./install-sh -c -d'
oldincludedir='/usr/include'
pdfdir='${docdir}'
prefix='NONE'
program_transform_name='s,x,x,'
psdir='${docdir}'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE_NAME "u3-tool"
#define PACKAGE_TARNAME "u3-tool"
#define PACKAGE_VERSION "0.3"
#define PACKAGE_STRING "u3-tool 0.3"
#define PACKAGE_BUGREPORT "daviedev@users.sourceforge.net"
#define PACKAGE "u3-tool"
#define VERSION "0.3"

configure: exit 1

---

### Post by evilbellylint on 2011-04-25
While I'm awaiting a response from my more linux savvy forumites, I'll go ahead and
try to teach myself how to properly set the variables to get ./configuration (as well as
'make install' ) to work :redface:

thanks in advance for all the help,

EBL

---

### Post by evilbellylint on 2011-04-25
forgive me if this is a dumb question, but I did a bit of "RTFM-ing" and this U3 Removal tool
doesn't appear to require anything different than the standard 

1) ./configure
2) make
3) make install

...is it unusual then that this SliTaz distro doesn't appear to include a simple 
Linux C compiler?


EBL

---

### Post by evilbellylint on 2011-04-25
(k...downloading gcc-4.4.1 and will install it to see if I can get this U3 Removal tool
to compile first...)

---

### Post by mörgæs on 2011-04-25
U3-tool is in the repositories. There is no need for compiling.

---

### Post by evilbellylint on 2011-04-25
@ mörgæs - sorry if I was confusing... I did d/l it from the repos, but upon attempting to
install it, xterm returned the error that "no acceptable C compiler found in $PATH"

- which led me to believe it was looking for gcc 

- which is what prompted me to d/l gcc & install it


So what does this error message imply? For some reason this SliTaz distro won't allow me
to install the u3-tool, apparently based on the above error message :confused:

---

### Post by Dutch70 on 2011-04-25
gcc is also in the repo's. Open your package manager *(not sure what that is in slitaz)* and search for "gcc". The package you need should say something like "The GNU C compiler".

---

### Post by evilbellylint on 2011-04-25
yeah, I d/l'd both the u3-tool & gcc from the repos, the problem I'm having is properly installing them, for some reason - most likely due to the fact that this sliTaz distro is on a read-only cd, and even though it loads itself entirely into RAM, whenever I've attempted to install a package, I get a spinning curser for a while - implying the package is being installed - and then I'm unable to run the newly installed package. (hence why I'm so intent on fixing this U3 issue so I can dump this SliTaz cd and make a live USB install of my choosing...)

so, in summary, here's where I'm at:

1) I've already created a live USB stick with a minimal distro that I planned on adding 
packages to as needed.

2) My HP refuses to boot from the live USB stick, even though it's properly formatted, 
flagged as 'boot' etc., etc...

3) I do believe the issue lies in removing the U3 code from the USB stick 

4) SliTaz itself does not carry the u-3 removal tool on its own mirrors, so I had to d/l
it (and gcc) from the general repos.

5) But now I can't seem to get gcc or u3-tool to properly install so I can remove the
offending U3 code from the USB stick in order for my HP laptop to boot from it :confused::confused::confused:

Either I'm missing something utterly basic, or this is becoming unnecessarily
complicated... it seems that regardless of SliTaz being non-persistent, it should
allow me to install other packages - albeit temporarily - until I reboot, no????


EBL

ADDENDUM: Correction, SliTaz did have gcc on its mirrors; it was only the u3-tool I had to d/l
from Sourceforge.

---

### Post by evilbellylint on 2011-04-25
ugh...still striking out on getting the u3-tool to install. Even with gcc successfully installed,
when I go to ./configure u3-tool I get the same "no acceptable C compiler found in $PATH"
error. How to I get u3-tool to recognize that gcc IS in fact installed?

I'm assuming it has something to do with the fact that the u3-tool package resides on my
desktop, while (I'm assuming) gcc was installed into RAM (as I'm running SliTaz off a CD...)

:confused::confused::confused::confused:

Thanks again for all the help.

EBL

---

### Post by Quackers on 2011-04-25
> **evilbellylint said:**
> hahaha...sorry. Right here!

Well, as soon as I rebooted and tapped F9 it was clear I'd already tried this option.
F9 does indeed call up the Boot Manager -- problem is only a single option is listed:

[B][COLOR=Blue]Boot Option Menu

Internal CD/DVD ROM Drive[/COLOR][/B]


I again tapped F10 to enter BIOS setup ->System Configuration->Boot Options
and the only options listed above [COLOR=Blue]**>Boot Order **[/COLOR]are:

[COLOR=Blue][B]CD-ROM Boot <Enabled>
Floppy Boot <Enabled>
Internal Network Adapter <Disabled>[/B][/COLOR]

And beneath, I have [COLOR=Blue]**>Boot Order **[/COLOR]set as follows:

[COLOR=Blue][B]Boot Order

USB Diskette on Key/USB Hard Drive
USB Floppy
Internal CD/DVD ROM Drive
USB CD/DVD Hard Drive
Notebook Hard Drive[/B][/COLOR]

In observing the "flashing light" on the USB stick, it's apparent the system is not recognizing the USB device in time for it to be listed as a boot option when tapping 
F9 to call up the Boot Manager....

Unless my eyes are deceiving me, you don't appear to have a USB flash drive boot device option. Would HP refer to one as a USB Diskette on Key? Strange if they do.

---

### Post by evilbellylint on 2011-04-25
@ Quackers

Their wording is indeed strange - I'm thinking perhaps their reference to "USB Hard Drive"
may in fact include removable media, as this laptop is certainly not what one would
consider "old" or outdated by any stretch. With all of the other features it has, I'd be
shocked if HP crippled this model by disabling USB flash drive booting.

I eventually did see "Sandisk" list in the Boot Manager options (F9) - not sure how or why
it suddenly decided to appear, but there it was, so more reason for my belief that it's at
least possible... I just haven't been able to succeed in getting it to boot from it yet due to
the U3 firmware conflict...

(which I'm STILL trying to resolve)


EBL

---

### Post by Hedgehog1 on 2011-04-25
On my HP dv8, the USB boot option only appears if a valid, bootable USB stick has already been inserted into a USB port.

This is why my instructions were to insert the USB stick before turning it on (or rebooting), and then it will appear after pressing F9.

If it does not appear in the list, it is not a valid boot USB.

I am dual booting Win7 and Natty on my dv8, and Natty was installed using F9 to boot from the USB.


***The Hedge***

:KS

---

### Post by Quackers on 2011-04-25
Turn it off, insert the usb flash drive, turn it on and look in bios.
Try every usb port.

---

### Post by evilbellylint on 2011-04-25
Thanks all. I'm able to get my laptop to see the USB stick in the Boot Manager now,
just still having troubles getting the U3 removal tool (u3-tool) from sourceforge to
install... a bit frustrating, but still trying. If anyone has advice as to what I am doing
wrong (particularly with respect to why u3-tool doesn't recognize that I have gcc
installed, and keeps returning the error "no acceptable C compiler found") I would
greatly appreciate the benefit of your experience.

EBL

---

### Post by collisionystm on 2011-04-25
I have a 16GB U3, a 4gb U3 and an 8.

I have never had a problem loading a live distro.

If installing from windows use 'Pen Drive Linux'.

Google it.

---

### Post by Dutch70 on 2011-04-25
If it see's it now & it didn't before, you may be able to boot from it without having to do anything else.

---

### Post by evilbellylint on 2011-04-25
@ Dutch70 - unfortunately, that's the frustrating part. The moment I saw "Scandisk"
listed in the Boot Manager at startup, I selected it and tapped ENTER - only to get
the same error message about not finding a boot device....

---

### Post by Dutch70 on 2011-04-25
You did verify the md5sum, right? 
[[COLOR="RoyalBlue"]HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")

Is there any way for you to check your usb with another computer? 

This just ins't making much sense. It makes you think it may be one of those situations where you work on the stereo for 2 hours only to realize you didn't have the volume up. Yes, I've done that. :P

---

### Post by Hedgehog1 on 2011-04-26
> **Dutch70 said:**
> It makes you think it may be one of those situations where you work on the stereo for 2 hours only to realize you didn't have the volume up. Yes, I've done that. :P

I am so glad I am not the only one... The receiver was on 'Mute', but it was the same principle...

***The Hedge***

:KS

---

### Post by mörgæs on 2011-04-26
Have you checked that you are using the newest BIOS on your computer?

---

### Post by evilbellylint on 2011-04-28
@ mörgæs - yes, that was one thing I checked even before attempting this.

It's still a mystery to me... I can see the USB stick listed in the Boot Manager
when I tap F9 during start-up, but the moment I select it and tap ENTER, I get
the same message that there are no bootable devices....

](*,)

---

