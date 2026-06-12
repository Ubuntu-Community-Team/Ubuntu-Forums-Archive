---
title: "Reverting to 2.6.20 kernel in gutsy"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by seldomridgej on 2007-10-23
I've got a question.  Is there a way to install an older kernel.  The reason I need to do this is because the newest kernel is missing an ndiswrapper module.  I need to get back to the 2.6.20.  Any help would be greatly appreciated.

---

### Post by vambo on 2007-10-23
Doesn't it show in your grub menu at bootup???

---

### Post by seldomridgej on 2007-10-23
I haven't looked, but i figured that it would not since its a clean install of gutsy.  I thought it would only come with the latest kernel.

edit:  no it isn't there.  And i can't find it in synaptic with the backport repositories enabled.

---

### Post by vambo on 2007-10-23
So under /boot 2.6.22-14 is your only kernel? Find that odd I must say, even with a clean install

---

### Post by seldomridgej on 2007-10-23
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6d9b2780-41ff-4d5c-9481-8cf98ce2b453 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6d9b2780-41ff-4d5c-9481-8cf98ce2b453 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by vambo on 2007-10-23
OK, that your menu.lst. What's under /boot?

```
ls /boot
```

---

### Post by seldomridgej on 2007-10-23
$ ls /boot

abi-2.6.22-14-generic
initrd.img-2.6.22-14-generic.bak
config-2.6.22-14-generic
memtest86+.bin
grub
System.map-2.6.22-14-generic
initrd.img-2.6.22-14-generic
vmlinuz-2.6.22-14-generic

---

### Post by vambo on 2007-10-23
I did find 2.6.20.16 in Synaptic. Just one thing, I'm assuming if you download it your current kernel will be replaced. Also, I'm no expert on this. What you do need though is the Feisty kernel under boot, then you can grub-update. It's the getting hold of the old kernel that's got me a bit stuck.

---

### Post by seldomridgej on 2007-10-23
I wouldnt mind if the kernel was completely replaced, its a clean install and theres no loss.  Willing to try anything.

---

### Post by vambo on 2007-10-23
OK, doing a search in Synaptic with "2.6.20" yields 
> linux-image-2.6.20-16-generic
Linux kernel image for version 2.6.20 on x86/x86_64
So hopefully if you get hold of it you can use it ok.

EDIT: There's also this guide on rolling your own [http://ubuntuforums.org/showthread.php?t=56835&highlight=kernel+thread]("http://ubuntuforums.org/showthread.php?t=56835&highlight=kernel+thread")

---

### Post by seldomridgej on 2007-10-23
could you post your apt sources list from /etc/apt  because i cant find those in synaptic.

---

### Post by vambo on 2007-10-23
OK, here it is. Basically it was generated from my Gutsy upgrade. Haven't had to change it since.

> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
# deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
# deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

# deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main

# deb [http://download.tuxfamily.org/pollyrepo](http://download.tuxfamily.org/pollyrepo) feisty/
# deb-src [http://download.tuxfamily.org/pollyrepo](http://download.tuxfamily.org/pollyrepo) feisty/


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe #Added by software-properties
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
################################
# Ubuntu Font Improvement Patch
# deb [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts
# deb-src [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts
################################




---

### Post by vambo on 2007-10-23
One last thought. You don't have a file > vmlinuz.old on your system do you? If you do it should point to the old kernel (it's a symlink).

---

### Post by Jonathan2007 on 2007-10-24
@ vambo I don't think you understand what he is saying. From what I gathered he did not upgrade from Feisty to Gutsy. Instead he did a complete format and fresh install of Gutsy. He would like to go back to an old kernel (the one in Feisty that is not available in Gutsy). He needs some Feisty repository I think in order to find the kernel he wants.

I am trying to use a new version of ndiswrapper (1.49) that I got installed through some Debian repository. The current kernel modules in Gutsy only allow up to version 1.45 I guess so I am also trying to downgrade my kernel and kernel modules to the ones in Feisty (which evidently allow a newer ndiswrapper version).

---

### Post by crisponions on 2007-10-24
I am trying to this exact same thing since 2.6.22 is playing like crap with vmware (tickless no working well).

---

