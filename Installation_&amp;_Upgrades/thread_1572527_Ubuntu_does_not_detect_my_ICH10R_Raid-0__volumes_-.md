---
title: "Ubuntu does not detect my ICH10R Raid-0  volumes - need to install Dual boot"
date: 2010-09-11
forum: Installation &amp; Upgrades
---

### Post by keplenk on 2010-09-11
Hi all,

I'm trying to install Ubuntu 10.04 64-bit on my 2 x 500gb Samsung F3s which are setup in RAID-0 divided in two Volumes.  First Volume is 750GB (Windows) and the 250gb is for Ubuntu.  I've already installed Windows (first primary partition) and after doing so, I booted the live CD of Ubuntu and the installer does not detect my 250GB 2nd raid volume.  I've tried Gparted but it only sees my HDDs separately -- not the 250gb raid volume. 

I've done research and some people suggested downloading the alternate CD and it prompted me that it detects RAID and asked me to install drivers for it.  I did but still it did not help.   

I've tried a different distro (linux mint and debian) and right off the bat it asked me to install RAID drivers but I think it is only software raid because after saying yes, i see a combined raid volume but not my 750gb or my 250gb.  Just 1 whole unpartitioned volume so it is no help.

Is there a way to install Ubuntu on an Intel RAID setup?  I know I've managed to install Ubuntu in a hardware raid solution before but it was a Jmicron RAID one (my very old pc). I know I'm just missing something here with this Intel Raid one.

Unfortunately, I don't want to give up my Intel RAID because it gives major performance difference between a NON-raid.

Please help.  I can't live without linux on my system.

Thanks!

EDIT:  By the way, could someone explain to me about what is a fakeraid/dmraid?  Is an intel ICHx-R chipset considered "fakeraid"?

---

### Post by ronparent on 2010-09-11
dmraid=fakeraid  It is merely the program used by linus based systems to recognize and access the so-called fakeraid drives. The main distinguishing feature between a fakeraid and software raid is that fakeraid was originall implemented by windows, later adapted by linux systems, and, as such can be used by either windows using special driver or linux using dmraid to access an established raid. A linux software raid can be accessed only thru linux systems using linux mdadm. A true hardware raid is usable only on OS's for which a driver is provided by the manufacturer. 

The short answer to your basic question is that the desktop distribution of 10.04 is not normally installable to a raid. It can be though. To do so, you need to boot to the live cd, install kpartx to the session, start the installer in the session and do a manual install. To install grub 2, in what is now step 8 of 8 of the install you have to select the advanced box and specifically select where you want the boot loader installed. If to the raid itselt, that must be selected. It cannot be installed to a component drive for the raid or to a raid partition (except for a special case if you know what you are doing). If the grub boot loader install fails you have to fix it by reinstalling grub from the live cd to make the newly installed system bootable. 

The same limitations and fixes apply to Mint 9 because that is based on Ubuntu 10.04. Ubuntu releases prior to 9.10 have other behavioral differences in installing to raids and you would need to consult the Fakeraid HowTo. The 9.10 desktop is installable to raid. In the future, the 10.10 which is now in beta developmental release appears to be fully installable to a fakeraid, but will have other developmental glitches until sometime after the final release in October. The bottom line is that I am now comfortable with my raid 0 10.04 and 10.10 installs but have gotten there only after working at it (at its current state 10.10 installs to raid as easily as Win7). If you are an advanced linux user I have given you enough you can probably do it on your own. If you need it, you can post your questions and I can provide more detail. Good luck.

---

