---
title: "USB wifi issues"
date: 2005-04-22
forum: Installation &amp; Upgrades
---

### Post by megsona on 2005-04-22
Newbie question time I'm afraid. Ubuntu is my first installation of Linux so bear with me, it's all new.

I have a ZD1211 usb wifi dongle, I got the Linux drivers from sourceforge ok. Tried to install then realised there's no kernel /usr/src/linux. So I got the kernel source tar from kernel.org, linux-2.6.10.tar.bz2, I think this is the right one. I also "think" I've installed it ok, and created a symbolic link making my /usr/src/linux directory ok. Now when I run the make for the zd1211 drivers I get the following errors

/lib/modules/2.6.10/build
/home/megsona/Zydas/zd1211
-I/home/megsona/Zydas/zd1211/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -Wno-unused -pipe -DAMAC -DGCCK -DOFDM -DUSE_EP4_SET_REG -DfTX_GAIN_OFDM=0
make -C /lib/modules/2.6.10/build SUBDIRS=/home/megsona/Zydas/zd1211 modules
make: *** /lib/modules/2.6.10/build: No such file or directory.  Stop.
make: *** [all] Error 2

I've checked the directory structure and /lib/modules/2.6.10/build does not exist, should the makefile script not create it though? My tree looks like this.

lib
__modules
_____2.6.10-5-386
_____boot
_____initrd
_____kernel


All the similar threads I've seen on this assume you've got a net connection so I'm left to do things by hand.

Any help much appreciated,

---

### Post by alastair on 2005-04-22
You probably only need to install the Ubuntu kernel headers - skip the kernel.org tar files for the moment i.e. install from an apt repo (use synaptic, say) :

linux-headers-<VERSION>

where <VERSION> matches your running kernel (mine is "2.6.10-4").

Then try the module build again.

---

### Post by megsona on 2005-04-23
Thanks for your reply, I got the headers installed ok via Synaptic. However I'm still getting the same error when trying to run the Makefile.
------------------------------------------------------------------------
root@ubuntu:/home/megsona/Zydas/zd1211 # make
/lib/modules/2.6.10/build
/home/megsona/Zydas/zd1211
-I/home/megsona/Zydas/zd1211/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -Wno-unused -pipe -DAMAC -DGCCK -DOFDM -DUSE_EP4_SET_REG -DfTX_GAIN_OFDM=0
make -C /lib/modules/2.6.10/build SUBDIRS=/home/megsona/Zydas/zd1211 modules
make: *** /lib/modules/2.6.10/build: No such file or directory.  Stop.
make: *** [all] Error 2
root@ubuntu:/home/megsona/Zydas/zd1211 #
------------------------------------------------------------------------

I've been trying to step through the Makefile to see what's up and noticed something odd. The line

------------------------------------------------------------------------
make: *** /lib/modules/2.6.10/build: No such file or directory.  Stop.
------------------------------------------------------------------------

is lookinf for 2.6.10/build, the script is using uname -r to get the release number to put in the path string but when I run uname -r from a console I get

--------------------------------------------------------------------------
root@ubuntu:/home/megsona/Zydas/zd1211 # uname -r
2.6.10-5-386
--------------------------------------------------------------------------

I may be focusing on something irrelevant though, guidance would again be appreciated. I've attached the Makefile script so you can see what I'm on about.

Thanks

---

### Post by alastair on 2005-04-23
Yes, the "build" directory, for me, is under :

/lib/modules/2.6.10-5-386/build/

Do you have this?

My "uname -r" is the same as yours :

2.6.10-5-386

So - why does your Makefile "$(shell uname -r;)" still return 2.6.10 ?

Try a :

make clean

You can also just edit the Makefile and change :

KERNRELEASE := $(shell uname -r;)

to

KERNRELEASE=2.6.10-5-386

(make a BACKUP copy first)

---

### Post by megsona on 2005-04-25
Did a fresh build of Ubuntu (wasn't booting, I think because I'd been messing with the kernel), didn't bother with the kernel install - just installed the headers and build-essential packages. Then amended the Makefile to point the 2.6.10-5-386 directory as you suggested. Success!

All I need to do now is figure out how to configure it. Quite glad it didn't go smoothly, learned alot from poking about, I'm feeling more uncomfortable booting into Windows now.

Thanks for your help, much appreciated.

---

### Post by megsona on 2005-04-29
Hi there, back again. I've got my wifi up and running now, all good. However each time I boot I have to re-enter the network ESSID name and WEP key. I know this must be an obvious one but which file do I edit for this to be configured at bootup?

thanks

---

### Post by alastair on 2005-04-29
/etc/network/interfaces

e.g.

wireless_essid <ESSID>
wireless_key <KEY>

See: man interfaces

---

### Post by megsona on 2005-04-29
Thanks again. Next time I'll RTFM.

---

### Post by megsona on 2005-05-06
Hello again,

checked /etc/network/interfaces

the relevant iwconfig lines are in there just as I would enter them in a terminal window. However when I boot it sits on "Configuring network devices" (just after Configuring hotplug subsystem") for about a minute, says ok then continues. When the system comes up however I have no connectivity, if I check my config with iwconfig it shows my wlan0 with no settings, no essid or wep key. I enter them manually and it kicks back in.

Confused.

Thanks.

---

