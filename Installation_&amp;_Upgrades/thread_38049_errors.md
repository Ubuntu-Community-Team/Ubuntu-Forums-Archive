---
title: "errors ????????"
date: 2005-05-29
forum: Installation &amp; Upgrades
---

### Post by n21roadie on 2005-05-29
cd into the kernel source, make menuconfig and enable these options 


(gedit:8696): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
root@james:/usr/src/linux-2.6.11.9 # make menuconfig
make: gcc: Command not found
/usr/src/linux-2.6.11.9/scripts/gcc-version.sh: line 11: gcc: command not found
/usr/src/linux-2.6.11.9/scripts/gcc-version.sh: line 12: gcc: command not found
make: gcc: Command not found
  HOSTCC  scripts/basic/fixdep
/bin/sh: gcc: command not found
make[1]: *** [scripts/basic/fixdep] Error 127
make: *** [scripts_basic] Error 2


The present kernel configuration has modules disabled.
Type 'make config' and enable loadable module support.
Then build a kernel with module support enabled.

make: *** [modules] Error 1

-------------------------------------------------------------------------------------------------------



DSL Assistant version 1.0.3 copyright AVM 2002

The DSL Assistant is examining your DSL configuration...
ERROR: The CAPI driver is not installed, loaded or accessible!
james@james:~$

How do i install or check CAPI driver ?
-------------------------------------------------------------------------------------------------------


/usr/src/linux-2.6.11.9 # dir
arch     Documentation  init    MAINTAINERS  README          sound
COPYING  drivers        ipc     Makefile     REPORTING-BUGS  usr
CREDITS  fs             kernel  mm           scripts
crypto   include        lib     net          security

--------------------------------------------------------------------------------------------------------
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_hoary_universe_ binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
Add to n21roadie's Reputation   	Edit/Delete Message

You generally just need to click on the "Reload" icon in Synaptic.
If this doesn't work then post back with what happens.

Just more of the above ???

-------------------------------------------------------------------------------------------------------

---

### Post by cudaman73 on 2005-05-29
firstly, you don't have gcc installed it appears.. which would explain 

```
/usr/src/linux-2.6.11.9/scripts/gcc-version.sh: line 11: gcc: command not found
/usr/src/linux-2.6.11.9/scripts/gcc-version.sh: line 12: gcc: command not found
```

use apt-get or synaptic to install gcc.. that should solve your kernel compilation woes.

as far as the DSL assistant goes, i'd google for that error and see what other people have said/done with it.

as for backports, i don't use the ubuntuforums.org one, as it's overloaded. replace those debs with

```
deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted
```

---

### Post by n21roadie on 2005-05-30
Many thanks for the info and below is the result of install of gcc,

please note i am unable at present to use my usb dsl modem to browse the
net , with ubuntu ,and all my efforts so far is to configure / setup the usb modem,
i am still using wind*ws ( dual boot ) to post these questions,so any advice please
bear this in mind ,i can download files to one of my home network pc ,and after i boot into ubuntu , i could open the files but please advise if any extra commands are required by this method ?  

root@james:/home/james # sudo apt-get install gcc
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gcc-3.3
Suggested packages:
  manpages-dev autoconf automake libtool flex bison gcc-doc gcc-3.3-doc
The following NEW packages will be installed:
  gcc gcc-3.3
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/554kB of archives.
After unpacking 4415kB of additional disk space will be used.
Do you want to continue [Y/n]? y
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) hoary/universe  Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_hoary_universe_ binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-bac kports/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_di sts_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directo ry)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-bac kports/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backport s_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or  directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-bac kports/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backpo rts_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such fil e or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-bac kports/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backpo rts_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such fil e or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-ext ras/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists _hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-ext ras/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_d ists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or direc tory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-ext ras/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports _dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or d irectory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-ext ras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports _dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or d irectory)
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) hoary/universe  Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_hoary_universe_ binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-bac kports/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_di sts_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directo ry)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-bac kports/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backport s_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or  directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-bac kports/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backpo rts_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such fil e or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-bac kports/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backpo rts_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such fil e or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-ext ras/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists _hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-ext ras/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_d ists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or direc tory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-ext ras/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports _dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or d irectory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-ext ras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports _dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or d irectory)

Preconfiguring packages ...
Selecting previously deselected package gcc-3.3.
(Reading database ... 58164 files and directories currently installed.)
Unpacking gcc-3.3 (from .../gcc-3.3_3.3.5-8ubuntu2_i386.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_3.3.5-1_i386.deb) ...
Setting up eagle-usb-utils (1.9.9-1) ...
dpkg: error processing eagle-usb-utils (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gcc-3.3 (3.3.5-8ubuntu2) ...
Setting up gcc (3.3.5-1) ...

Errors were encountered while processing:
 eagle-usb-utils
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) hoary/universe  Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_hoary_universe_ binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-bac kports/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_di sts_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directo ry)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-bac kports/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backport s_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or  directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-bac kports/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backpo rts_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such fil e or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-bac kports/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backpo rts_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such fil e or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-ext ras/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists _hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-ext ras/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_d ists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or direc tory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-ext ras/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports _dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or d irectory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-ext ras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports _dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or d irectory)
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@james:/home/james # cd /usr/src/
root@james:/usr/src # cd linux-2.6.11.9
root@james:/usr/src/linux-2.6.11.9 # make menuconfig
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/split-include
  HOSTCC  scripts/basic/docproc
  SHIPPED scripts/kconfig/zconf.tab.h
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/mconf.o
  SHIPPED scripts/kconfig/zconf.tab.c
  SHIPPED scripts/kconfig/lex.zconf.c
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/mconf
/usr/bin/ld: cannot find -lncurses
collect2: ld returned 1 exit status

>> Unable to find the Ncurses libraries.
>>
>> You must install ncurses-devel in order
>> to use 'make menuconfig'

make[2]: *** [scripts/lxdialog/ncurses] Error 1
make[1]: *** [menuconfig] Error 2
make: *** [menuconfig] Error 2
root@james:/usr/src/linux-2.6.11.9 # cd
root@james:~ # sudo apt-get install ncurses-devel
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) hoary/universe  Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_hoary_universe_ binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-bac kports/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_di sts_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directo ry)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-bac kports/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backport s_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or  directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-bac kports/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backpo rts_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such fil e or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-bac kports/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backpo rts_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such fil e or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-ext ras/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists _hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-ext ras/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_d ists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or direc tory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-ext ras/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports _dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or d irectory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-ext ras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports _dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or d irectory)
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) hoary/universe  Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_hoary_universe_ binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-bac kports/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_di sts_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directo ry)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-bac kports/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backport s_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or  directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-bac kports/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backpo rts_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such fil e or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-bac kports/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backpo rts_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such fil e or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-ext ras/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists _hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-ext ras/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_d ists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or direc tory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-ext ras/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports _dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or d irectory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-ext ras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports _dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or d irectory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package ncurses-devel

---

### Post by Boggles3 on 2005-07-16
try apt-get install libncurses? as root and see if that installs ncurses for you dorrectly

---

