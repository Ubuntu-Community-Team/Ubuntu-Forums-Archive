---
title: "[howto] tweaking a livecd in order to blacklist offending kernel modules"
date: 2008-10-24
forum: Installation &amp; Upgrades
---

### Post by eldragon on 2008-10-24
ive got one of the laptops affected by the following bug: [http://bugzilla.kernel.org/show_bug.cgi?id=9905](http://bugzilla.kernel.org/show_bug.cgi?id=9905)

with more info here: 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/187671](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/187671)


there has been a patch released to fix the issue, but the likeliness of it being included in the intrepid release is small, so ive decided to jump ahead and make a livecd that will boot in these laptops.

the procedure consist on the following:

[LIST]
[*]download a livecd
[*]extract it with archive manager
[*]use squashfs to uncompress the livecd filesystem
[*]edit /etc/modprobe/blacklist to blacklist the offending modules
[*]repack the livecd filesystem
[*]create a bootable iso
[*]burn
[/LIST]

first things first: you need to have squashfs-tools and genisoinage, so
```

$ sudo apt-get install squashfs-tools genisoimage

```


now we begin: download the livecd you wish to be able to boot.

then extract the contents of the livecd to a folder in your desktop called isofs using the archive manager.

next, open a terminal by pressing [alt]-[f2] and typing
```

gnome-terminal

```

and execute:
```

$ cd ~/Desktop
$ sudo unsquashfs ~/Desktop/isofs/casper/filesystem.squashfs

```

which will uncompress the livecd filesystem so that we can modify it.

now we edit the blacklist file with
```

$ sudo gedit ~/Desktop/squashfs-root/etc/modprobe.d/blacklist

```

and add to the end of the file the following lines:
```

blacklist sdhci
blacklist sdhci-pci

```


next step involves rebuilding the squashfs

```

$ sudo rm ~/Desktop/isofs/casper/filesystem.squashfs
$ sudo mksquashfs ~/Desktop/squashfs-root ~/Desktop/isofs/casper/filesystem.squashfs

```

and we make sure we can read the file when creating the iso:
```

$ sudo chmod a+r ~/Desktop/isofs/casper/filesystem.squashfs

```

next step involves creating the bootable cdrom image:

```

$ cd ~/Desktop/isofs
$ mkisofs -o ~/Desktop/livecd_nosdhci.iso -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -J ~/Desktop/isofs/

```

finally, burn the image livecd_nosdhci.iso with brasero, and test it :D

---

### Post by pablomme on 2008-10-24
I haven't tried following your instructions, but I've spotted two little mistakes:

First, by "open a terminal, [alt]-[f2] and type ..." I think you mean "open a terminal by pressing [alt]-[f2] and typing ..." (else you open a terminal and from there you open a terminal..).

Second, ~\Documents should be ~/Documents.

I'll let you know if I try this out and find any other hiccups (this will be in a week's time).

Thanks for doing this.

---

### Post by eldragon on 2008-10-25
> **pablomme said:**
> I haven't tried following your instructions, but I've spotted two little mistakes:

First, by "open a terminal, [alt]-[f2] and type ..." I think you mean "open a terminal by pressing [alt]-[f2] and typing ..." (else you open a terminal and from there you open a terminal..).

Second, ~\Documents should be ~/Documents.

I'll let you know if I try this out and find any other hiccups (this will be in a week's time).

Thanks for doing this.

thanks, i fixed both mistakes. :D

i did manage to get a working live cd with this :D

---

### Post by pablomme on 2008-10-27
Ok, I've tried this now. Here is a slightly modified howto which uses sudo only when strictly required, and incorporates some tips from the Ubuntu Wiki page on [liveCD customization](https://help.ubuntu.com/community/LiveCDCustomization).

** 1. Open a terminal**

You can open it from Applications > Accessories > Terminal, or alternatively pressing Alt+F2 and typing gnome-terminal in it.

** 2. Enter sudo password**

Type
```

sudo -v

```
and enter your password.

** 3. Install things**

To make sure you have all the programs you need, type
```

sudo apt-get install squashfs-tools genisoimage fakeroot file-roller

```

** 4. Set up**

Type this, changing the values of the variables to specify what you want to do:
```

ORIG_IMAGE=~/Desktop/ubuntu-8.10-rc-desktop-i386.iso
MOD_IMAGE=~/Desktop/ubuntu-8.10-rc-desktop-i386-nosdhci.iso
MOD_LABEL="Ubuntu 8.10 i386"
TEMP_DIR=~/tmp

```
ORIG_IMAGE should point at the ISO file you already have, and MOD_IMAGE says where to put the modified ISO. MOD_LABEL and TEMP_DIR can be safely left alone.

** 5. Proceed**

Copy this and paste it into your terminal verbatim:
```

mkdir -p "$TEMP_DIR/mod-distrib/ISO"
cd "$TEMP_DIR/mod-distrib"
file-roller -e ISO "$ORIG_IMAGE"
sudo unsquashfs ISO/casper/filesystem.squashfs
#START MODIFICATIONS
echo "# Local blacklist" > squashfs-root/etc/modprobe.d/blacklist.local
echo "blacklist sdhci" >> squashfs-root/etc/modprobe.d/blacklist.local
echo "blacklist sdhci-pci" >> squashfs-root/etc/modprobe.d/blacklist.local
#END MODIFICATIONS
rm ISO/casper/filesystem.squashfs
sudo mksquashfs squashfs-root ISO/casper/filesystem.squashfs -nolzma
sudo chown $USER ISO/casper/filesystem.squashfs
rm -rf squashfs-root
cd ISO
rm md5sum.txt
find . -type f -print0 | xargs -0 md5sum > md5sum.txt
fakeroot mkisofs -D -r -V "$MOD_LABEL" -cache-inodes -J -l -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o "$MOD_IMAGE" .
cd .. && rm -rf ISO
cd && rmdir "$TEMP_DIR/mod-distrib"

```
After a little wait the modified ISO will be on your desktop (or wherever you decided to place it), and all the messy temporary bits should have been cleared away. You can burn your ISO to a CD by double-clicking on it (provided you haven't explicitly modified this behaviour!)

If you need to do any other straight-forward modifications to the distribution (ie. add, remove or modify configuration files), do them between "#START MODIFICATIONS" and "#END MODIFICATIONS" above. Anything involving installing/removing packages requires a more sophisticated approach using a chroot cage as described in [the relevant wiki page](https://help.ubuntu.com/community/LiveCDCustomization), but the rest should remain valid.

---

### Post by eldragon on 2008-10-27
much cleaner aproach, thanks for the time..

ive installed intrepid and im having loads of problems in this laptop. have you had the chance to test intrepid out?

im starting to believe my cdrom might be on its way out and some files didnt copy correctly.

---

### Post by pablomme on 2008-10-27
I tried the live CD. The only thing I noticed was that network-manager (and its applet) had failed to start, after which I turned off the computer since there was little I could do without an internet connection..

---

### Post by eldragon on 2008-10-27
> **pablomme said:**
> I tried the live CD. The only thing I noticed was that network-manager (and its applet) had failed to start, after which I turned off the computer since there was little I could do without an internet connection..

using the same laptop from the bug report?

the network manager is of no use. since it needs the rt73usb driver, which isnt as effective as the legacy one from serialmonkey, even if it worked here, i dont use it, just compile the legacy drivers from serialmonkey and use rutilt to configure the wireless connection.

if thats the only problem you experienced, then i guess formatting and reinstalling with a new cd could prove fruitful...

---

### Post by pablomme on 2008-10-27
Same laptop, yeah. I've tried again, this time I had a problem with the X server, so I decided no to trust the CD and go with a memory stick, using [Unetbootin](http://unetbootin.sourceforge.net/) - very easy to use.

The X server problem went away when I booted from the memory stick, but the network-manager one remained.

> **eldragon said:**
> 
the network manager is of no use. since it needs the rt73usb driver, which isnt as effective as the legacy one from serialmonkey, even if it worked here, i dont use it, just compile the legacy drivers from serialmonkey and use rutilt to configure the wireless connection.


What do you mean? Why does network-manager need a USB driver?

---

### Post by eldragon on 2008-10-27
> **pablomme said:**
> Same laptop, yeah. I've tried again, this time I had a problem with the X server, so I decided no to trust the CD and go with a memory stick, using [Unetbootin](http://unetbootin.sourceforge.net/) - very easy to use.

The X server problem went away when I booted from the memory stick, but the network-manager one remained.



What do you mean? Why does network-manager need a USB driver?


the ralink wireless adapter in this notebook is actually a usb dongle wired to a usb hub inside the notebook :D

anyway, its of no importance. the truth is the included driver for our chispet is pants. it doesnt work as it should, BUT it works with the network manager, something i really wish i could use.

here, the network manager doesnt die. it works, but wireless signal is less than optimal. so i just blacklist rt73usb, rt2x00lib and and rt2x00usb.

i download the rt73 legacy driver [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz) which works much more consistenly but it isnt supported by the network manager.

you will need to build the driver but its fairly easy:
```

$ sudo apt-get install build-essential
$ make
$ strip -S rt73.ko
$ sudo make install
$ sudo apt-get install rutilt

```
execute rutilt to configure your wireless connection

thats all there is to it. you will find those drivers are much more stable.. yet, less compatible with the new way of doing things.

ive just installed again with a new cd. and still experiencing the same cpu fan effect. no thermal sensors found, and it spins constantly. arent you experiencing that?

---

### Post by pablomme on 2008-10-28
I think our laptops are different, then. Mine has an Intel PRO/Wireless 3945 card.

I didn't notice any other problems on the laptop, but again my focus was on the network-manager issue, so there may be other broken things and I just didn't realize..

Your fan problem reminds me of the one time I tried OpenSolaris, whose kernel doesn't have a cpufreq equivalent and the CPU frequency remained at its maximum, with the fan trying to cool it down constantly. Perhaps you should try to force-load the cpufreq module?

Anyway, between my laptop and my desktop (which suffers from a Radeon driver problem in Intrepid) this is going to be an "interesting" update process..

---

### Post by eldragon on 2008-10-28
> **pablomme said:**
> I think our laptops are different, then. Mine has an Intel PRO/Wireless 3945 card.

I didn't notice any other problems on the laptop, but again my focus was on the network-manager issue, so there may be other broken things and I just didn't realize..

Your fan problem reminds me of the one time I tried OpenSolaris, whose kernel doesn't have a cpufreq equivalent and the CPU frequency remained at its maximum, with the fan trying to cool it down constantly. Perhaps you should try to force-load the cpufreq module?

Anyway, between my laptop and my desktop (which suffers from a Radeon driver problem in Intrepid) this is going to be an "interesting" update process..

heh, i dont know why i thought all laptops affected by the sdhci fiasco were the same.

the cpu is throtling ok, ive got an applet that says so :D, anyway, right now the problem has gone away (???) there seems to be a race condition that doesnt happen when NM is not there :D quite an odd problem.

there are other issues concenring alsa not shutting down nicely and bootup network configuration through /etc/network/interfaces being really slow when a network isnt available during boot.

---

### Post by pablomme on 2008-11-19
Hey! I was wondering how your experience with Intrepid is going so far.

On my laptop I do find weirdnesses from time to time. I think I'm having your fan problem too, it happens at random and not very often. When it happens, my temperature sensor applet disappears from the gnome panel. I just had another weird problem where the system suddenly decided that the battery was completely empty (it was full, and the laptop charger was plugged in) and went into suspend...

Coincidentally, a friend of mine has a laptop with your wireless card which I configured to use the legacy rt73 driver and rutilt for management, after remembering what you had posted here. Heh..

---

### Post by eldragon on 2008-11-19
> **pablomme said:**
> Hey! I was wondering how your experience with Intrepid is going so far.

On my laptop I do find weirdnesses from time to time. I think I'm having your fan problem too, it happens at random and not very often. When it happens, my temperature sensor applet disappears from the gnome panel. I just had another weird problem where the system suddenly decided that the battery was completely empty (it was full, and the laptop charger was plugged in) and went into suspend...

Coincidentally, a friend of mine has a laptop with your wireless card which I configured to use the legacy rt73 driver and rutilt for management, after remembering what you had posted here. Heh..


hey, good news. i found a solution to most problems. its called arch.

yes, i got fed up waiting for some developer to even answer my bug reports.

arch can disable modules from grub which makes installing much easier..yet its more convoluted if you consider you got to configure almost everything. but i got rid of the fan control problem, which was a real pain in the rearend.

another plus, is that the kernel rt73usb driver works great under arch, i dont know whats the deal with the driver under ubuntu... i always thought it was the driver's fault, but it appears it was not.


beware of the fan problem. i had 3 different scenarios:

most times: fan would run non stop

some times: fan would run normally between 50C and 60C

a couple of times: fan would not run no matter what THRM said. cpu temp got as high as 70C before i realized and rebooted.

i didnt experience the battery problem, maybe it was a lose contact, i would reatach the battery to be sure (aka: remove, replace in)

suspend / hibernate froze the computer so :(. under arch, i didnt get to address the problem yet. it doesnt work, but it doesnt freeze the computer either.


one extra plus: the arch build system is EXELLENT. im loving it.


good luck

---

### Post by pablomme on 2008-11-19
Heheh.. good solution.

I'm sticking with Ubuntu, though. It has the big advantage of being very popular, which gets you better support for third-party applications than most other distros and massive forums like this one, and is in general balanced (not the fastest nor the slowest, not the most advanced nor obsolete, etc). Support in Launchpad is stalled right now, but I'm hoping that it will get better eventually.

Anyway, the battery problem may really be a physical disconnection as you say; actually I removed the battery hours before it happened to see if the replacement I bought fitted in correctly; maybe it didn't click in properly when I put the old one back in.

The fan is a bit of a mystery. I don't get anything in the logs to diagnose it.

As for the rt73usb issue, since you say Arch Linux's version works well, I'll try to dig what Ubuntu patches have been applied to it, to see if I can provide some clue in Launchpad (and have it fixed by 2010, heheh).. On my laptop I have a different wireless card which has a different issue (causing hard locks, no less!), but that is more or less fixable.

---

### Post by eldragon on 2008-11-19
> **pablomme said:**
> Heheh.. good solution.

I'm sticking with Ubuntu, though. It has the big advantage of being very popular, which gets you better support for third-party applications than most other distros and massive forums like this one, and is in general balanced (not the fastest nor the slowest, not the most advanced nor obsolete, etc). Support in Launchpad is stalled right now, but I'm hoping that it will get better eventually.

Anyway, the battery problem may really be a physical disconnection as you say; actually I removed the battery hours before it happened to see if the replacement I bought fitted in correctly; maybe it didn't click in properly when I put the old one back in.

The fan is a bit of a mystery. I don't get anything in the logs to diagnose it.

As for the rt73usb issue, since you say Arch Linux's version works well, I'll try to dig what Ubuntu patches have been applied to it, to see if I can provide some clue in Launchpad (and have it fixed by 2010, heheh).. On my laptop I have a different wireless card which has a different issue (causing hard locks, no less!), but that is more or less fixable.


i *think* and this is a big maybe. the fan problem is related to a race condition in the bootup process. might be related to the migration of some daemons to upstart. but im at a loss here. im way out of my league.

concerning the rt73usb issue, it must be related to patches related to the network manager, or the network manager itself.


about arch's software support. there is this thing called AUR (arch user repository), where you search for buid scripts provided by users.
these scripts can build, install, modify existing packages, check dependencies and fix them. its quite extensive, and its taking some time getting used to the way it works (in order to make your own PKGBUILD). but, lets just say....its better and safer than having some johndoe's repository in sources.list.

intrepid has been a bunk for me, if i had decided to try linux for the first time, and the cd i received was intrepid, id be back to windows in no time.

but what definately got me deciding i needed a new home was the whole SDHCI issue. i still cant believe the patch wasnt included in intrepid. ive posted a bug to the arch bug tracking system concerning the issue, ive been told not to hold my breath on it since its a dirty hack (the patch), but im still hoping.

ive referenced the kernel bug report and launchpad's entry. for devs to refer to the discussions. maybe someone there knows how to provide a descent fix.


EDIT
check the bugreport for the arch kernel here: [http://bugs.archlinux.org/task/12180?project=1](http://bugs.archlinux.org/task/12180?project=1) and please, comment anything i missed...

---

### Post by pablomme on 2008-11-21
> i *think* and this is a big maybe. the fan problem is related to a race condition in the bootup process. might be related to the migration of some daemons to upstart. but im at a loss here. im way out of my league.

I get the problem usually after several hours of uptime, I don't think it's related to the boot-up process.

> ive posted a bug to the arch bug tracking system concerning the issue, ive been told not to hold my breath on it since its a dirty hack (the patch), but im still hoping.

Perhaps this is the reason why it didn't make it into Intrepid? And us mentioning that there's work going on upstream to fix this probably just made them disregard it entirely. Our best shot is the kernel bugzilla, I think. I'll post again to remind the PCI expert about this issue.

> check the bugreport for the arch kernel here: [http://bugs.archlinux.org/task/12180?project=1](http://bugs.archlinux.org/task/12180?project=1) and please, comment anything i missed... 

It looks OK to me.

---

### Post by eldragon on 2008-11-21
ohh bugger. i got this thermal_zone folder empty again under arch. just once..but lets say its not upstart's fault. dang it. anyway, its much less frequent here. and arch works much better than ubuntu did anyway, so im sticking with it :D

about the patch itself. i dont think there will be any more movement anywhere, we are stuck with a half working live cd i guess. thanks god arch is a rolling release distro and i will never need a live cd (unless i break things...like i usually do :D)

---

### Post by eldragon on 2008-11-30
pablomme, today the arch kernel got bumped to 2.6.27.7 and checking the patchset for that kernel, they appear to have includded the h12y patch...gonna reboot with that kernel and report back to the appropiate places :D

im soo happy

---

### Post by steffi on 2009-04-19
i just tried this but I get an error when using file-roller that the image type isn't supported.

I also went thru the original HowTo also and noticed a couple of mistakes in that.

> **pablomme said:**
> Ok, I've tried this now. Here is a slightly modified howto which uses sudo only when strictly required, and incorporates some tips from the Ubuntu Wiki page on [liveCD customization](https://help.ubuntu.com/community/LiveCDCustomization).

** 1. Open a terminal**

You can open it from Applications > Accessories > Terminal, or alternatively pressing Alt+F2 and typing gnome-terminal in it.

** 2. Enter sudo password**

Type
```

sudo -v

```
and enter your password.

** 3. Install things**

To make sure you have all the programs you need, type
```

sudo apt-get install squashfs-tools genisoimage fakeroot file-roller

```

** 4. Set up**

Type this, changing the values of the variables to specify what you want to do:
```

ORIG_IMAGE=~/Desktop/ubuntu-8.10-rc-desktop-i386.iso
MOD_IMAGE=~/Desktop/ubuntu-8.10-rc-desktop-i386-nosdhci.iso
MOD_LABEL="Ubuntu 8.10 i386"
TEMP_DIR=~/tmp

```
ORIG_IMAGE should point at the ISO file you already have, and MOD_IMAGE says where to put the modified ISO. MOD_LABEL and TEMP_DIR can be safely left alone.

** 5. Proceed**

Copy this and paste it into your terminal verbatim:
```

mkdir -p "$TEMP_DIR/mod-distrib/ISO"
cd "$TEMP_DIR/mod-distrib"
file-roller -e ISO "$ORIG_IMAGE"
sudo unsquashfs ISO/casper/filesystem.squashfs
#START MODIFICATIONS
echo "# Local blacklist" > squashfs-root/etc/modprobe.d/blacklist.local
echo "blacklist sdhci" >> squashfs-root/etc/modprobe.d/blacklist.local
echo "blacklist sdhci-pci" >> squashfs-root/etc/modprobe.d/blacklist.local
#END MODIFICATIONS
rm ISO/casper/filesystem.squashfs
sudo mksquashfs squashfs-root ISO/casper/filesystem.squashfs -nolzma
sudo chown $USER ISO/casper/filesystem.squashfs
rm -rf squashfs-root
cd ISO
rm md5sum.txt
find . -type f -print0 | xargs -0 md5sum > md5sum.txt
fakeroot mkisofs -D -r -V "$MOD_LABEL" -cache-inodes -J -l -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o "$MOD_IMAGE" .
cd .. && rm -rf ISO
cd && rmdir "$TEMP_DIR/mod-distrib"

```
After a little wait the modified ISO will be on your desktop (or wherever you decided to place it), and all the messy temporary bits should have been cleared away. You can burn your ISO to a CD by double-clicking on it (provided you haven't explicitly modified this behaviour!)

If you need to do any other straight-forward modifications to the distribution (ie. add, remove or modify configuration files), do them between "#START MODIFICATIONS" and "#END MODIFICATIONS" above. Anything involving installing/removing packages requires a more sophisticated approach using a chroot cage as described in [the relevant wiki page](https://help.ubuntu.com/community/LiveCDCustomization), but the rest should remain valid.

---

### Post by eldragon on 2009-04-19
> **steffi said:**
> i just tried this but I get an error when using file-roller that the image type isn't supported.

I also went thru the original HowTo also and noticed a couple of mistakes in that.

explain further

---

### Post by msktje on 2009-05-01
i wanted to boot the jaunty livecd but the kernel freezes. I found out that it came from my sound card "ess maestro" and that the bug can be worked arround by blacklisting radio_maestro. ( [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/357724](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/357724) )

i have tried the first method. I only changed one bit:

> **eldragon said:**
> ive got one of the laptops affected by the following bug: [http://bugzilla.kernel.org/show_bug.cgi?id=9905](http://bugzilla.kernel.org/show_bug.cgi?id=9905)

now we edit the blacklist file with
```

$ sudo gedit ~/Desktop/squashfs-root/etc/modprobe.d/blacklist

```



to

```

$ sudo gedit ~/Desktop/squashfs-root/etc/modprobe.d/blacklist.conf

```

because otherwise it creates an non existing file blacklist. I haven't tried it like that but using blacklist.conf works.

> **steffi said:**
> i just tried this but I get an error when using file-roller that the image type isn't supported.


I also experienced that problem. It was easily fixed because eventhou i putted the iso on the desktop, the link to the desktop was not ~/desktop/xxx.iso but ~/bureaublad/xxx.iso due to a translated ubuntu.

i have also tried the second method. That didn't work for me.
The first time i have tried that i specified my ~/tmp to another partition. That gave me errors about UID changes that couldn't be performed. **So the ~/tmp has to be on the same partition**.

the second time i putted the ~/tmp on the same partition but now i got that the modifications could not be made to the blacklist.local I haven't tried it again but i suspect that it is because blacklist.local doesn't exist for the jaunty iso. I don't know if it existed on intrepid. 
I will try it again with 
```

echo "blacklist radio_maestro" >> squashfs-root/etc/modprobe.d/blacklist.conf

```
when the iso of the new crunchbang linux arrives and let you know.

---

