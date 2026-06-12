---
title: "Can't compile 20.04 LTS kernel with increased CONFIG_DVB_MAX_ADAPTERS"
date: 2020-09-25
forum: Installation &amp; Upgrades
---

### Post by faroutliving on 2020-09-25
Not my first rodeo, but certainly not an expert on this. I've been compiling custom kernels for over 5 years for a server I have 4 quad tv tuner cards in. The default kernel has CONFIG_DVB_MAX_ADAPTERS set to 8, and I usually increase it to 32. Yesterday I decided it was time to bite the bullet and install 20.04 on that machine.

First, [https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel) still doesn't work for me to get the source package. I suppose I could get it via git, but ran into a different set of problems (git package relies on SSL 1.0.0, and only 1.1.0 is installed on this machine. Had to hand copy 1.0.0 from another machine just to get git to clone for another task). Either way, not the problems I am reporting today.

I don't recall now what steps got me the source. Basically installed a Ubuntu package that got me linux-source-5.4.0, decompressed the source archive inside and moved the contents to the root of the linux-source-5.4.0 folder like I usually have done through the years.

After doing these basic steps (like always, these are from my notes):

chmod a+x debian/rules
chmod a+x debian/scripts/*
chmod a+x debian/scripts/misc/*
fakeroot debian/rules clean
fakeroot debian/rules editconfigs

# edit config:amd64/config.flavour.generic? YES
# change Device Drivers -> Multimedia support (now you have to scroll down to see this option) -> maximum number of DVB/ATSC adapters to 32
# tab to <Save> at the bottom and press return.
# tab to choose the default .config file and press return.
# press return to close the "completed" dialog.
# press Esc Esc to go to the Device Drivers.
# press Esc Esc to go to the top menu.
# Press Esc Esc to exit
# Choose NO for the rest of the edit choices

# edit kernel name
nano debian.master/changelog

# add +32dvb to version number on first line ie: (5.4.0-48.52) becomes (5.4.0-48.52+32dvb)

I then had to set C_INCLUDE_PATH=/usr/include to get past a new issue and start again. Then after a few minutes it manages to build the headers.deb file and then throws:

check-config: FAIL (32 != 8): CONFIG_DVB_MAX_ADAPTERS policy<{'amd64': '8', 'arm64': '8', 'armhf': '8', 'i386': '8', 'ppc64el': '8', }>

and stops! Clearly 32 != 8 (no new math here)... Obviously the point of configuration is to change the defaults...

Any advice welcome. Thanks!

Deron

---

### Post by norobro on 2020-09-25
[SIZE=2]Caveat: it's been a while since I have compiled a kernel. 

I found the following info regarding "CONFIG_DVB_MAX_ADAPTERS":> Maximum number of DVB/ATSC adapters. Increasing this number
increases the memory consumption of the DVB subsystem even
if a much lower number of DVB/ATSC adapters is present.
Only values in the range 4-32 are tested.


If you are unsure about this, use the default value 16


Symbol: DVB_MAX_ADAPTERS [=8]
Type : integer
Range : [1 255I searched some but couldn't find anything on why Debian/Ubuntu set the default to 8.


You can try modifying the file "debian.master/config/config.common.ubuntu" ```
CONFIG_DVB_MAX_ADAPTERS=8
```If that doesn't work try changing this line in "debian.master/config/annotations"```
CONFIG_DVB_MAX_ADAPTERS                         policy<{'amd64': '8', 'arm64': '8', 'armhf': '8', 'i386': '8', 'ppc64el': '8', }>
```
After all the build is failing anyway,  so what can it hurt. Good luck.[/SIZE]

---

### Post by faroutliving on 2020-10-01
Thanks norobro, That is pretty much what I did and it did let me compile it. Why editconfigs did not get the job done this time is above my pay grade, but at least I could compile a new kernel and install it. Thanks again!

---

