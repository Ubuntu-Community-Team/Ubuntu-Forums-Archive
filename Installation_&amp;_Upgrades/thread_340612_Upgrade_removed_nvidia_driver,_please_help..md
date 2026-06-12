---
title: "Upgrade removed nvidia driver, please help."
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by N'Jal on 2007-01-17
Bit of an odd problem, this morning I booted ubuntu edgy eft and found there were some updates that needed installing, so I let update-manager do it's work and low and behold when I rebooted later on in the day I found that the upgrade had removed nvidia-glx, all attempts to reinstall this package have resulted in the error message that nvidia-glx requires nvidia-kernel-common, which is not installable. 

The nv driver does not work on my system so I am forced to use the vesa driver for now, so if someone might be able to point out where my system might have gotten confused, and how I might go about fixing it, I would be mighty appriciative.

Something else of interest was that the linux-restricted-modules-2.6.17-10-generic was installed as X86_64 which is curious, since I only have a 32 bit chip, I have not attempted to remove this package and install the 32 bit one yet. I am not all that confident in attempting to fix Linux, so if it's a simple as replaceing the packages for the right architecture fair enough, but can someone first confirm?

However I was using the beta nvidia driver for a while so this may have something to do with it, if so, here is my apt sources list in case some of the repo's have been shut down.

```

# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted #Added by software-properties


# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy

deb http://gb.archive.ubuntu.com/ubuntu/ edgy main multiverse restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main multiverse restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main multiverse restricted #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main universe multiverse restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main universe multiverse restricted #Added by software-properties


deb http://security.ubuntu.com/ubuntu edgy-security main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu edgy-security universe

## nVidia Binary Driver
deb http://albertomilone.com/drivers/edgy/nonlegacy/32bit binary/

## Beryl
deb http://ubuntu.beryl-project.org/ edgy main

## Murrine
deb http://malteo.homelinux.net edgy-malteo all
deb-src http://malteo.homelinux.net edgy-malteo all 

deb http://archive.ubuntu.com/ubuntu/ edgy-updates restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ edgy-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy-proposed restricted main multiverse universe #Added by software-properties

## Wine
deb http://wine.budgetdedicated.com/apt edgy main

## Skype
deb http://download.skype.com/linux/repos/debian/ stable non-free


```

---

### Post by allwin on 2007-01-17
I see you may have installed something called ENVY?  When crufty updates blow away my proprietary nVidia driver, I just go to a terminal and run ENVY and it downloads and re-installs the latest driver.  For me, it has always repaired the damage of some automatic update.  If you didn't use ENVY in the past to install your driver (I see albertomilone's repository there, which is why I asked)...then NEVER MIND!

---

### Post by N'Jal on 2007-01-18
Nope, envy is not present on my system, would it be advisable to install it, or find some other way to re-install the driver?

Thanks for the reply though, I didn't think I was going to get one. :S

---

### Post by mts-fi on 2007-01-18
I had to install nvidia driver too after kernel update.

I followed these instructions: [http://www.ubuntuforums.org/showthread.php?t=296933&highlight=nvidia+9742](http://www.ubuntuforums.org/showthread.php?t=296933&highlight=nvidia+9742)

Please read the wohle thread before installing!
9742 driver was a bit tricky to install and it didn't work so great tor me after kernel-update so I installed 9746 beta driver.

9746 is easy to install but I'm not sure if it works unles you have installed that 9742 driver too. Read my post added in that thread.

Now my nvidia works great, and someone else has installed 9746 driver too.

---

### Post by N'Jal on 2007-01-18
Ok this has gotten most of my issues fixed, but beryl wont work now, is this driver the latest one? Because beryl will only run atop the latest nvidia driver.

If it's not, any ideas on how to get beryl working again?

---

### Post by mts-fi on 2007-01-18
> **N'Jal said:**
> Ok this has gotten most of my issues fixed, but beryl wont work now, is this driver the latest one? Because beryl will only run atop the latest nvidia driver.

If it's not, any ideas on how to get beryl working again?

I think it's latest version.
Sorry I can't help you with beryl...

this might help you: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Edgy_with_nVidia](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Edgy_with_nVidia)

---

### Post by mahiyar on 2007-01-18
One thing I can tell Beryl does not need the latest Nvidia's driver, mine is way below your 9 series it 8746 or something and still beryl works. And if you use beta drivers of Nvidia, every time your kernel is upgraded or changed you will have to reinstall Nvidia drivers.

---

### Post by phansiizwe on 2007-01-18
As far as I know, Beryl only works DIRECTLY with Nvidia driver version 9746.
For the older drivers you will still need to install XGL.

I held back on the latest nvidia-glx, linux-restricted-modules-*, xserver-xorg-* updates, but I will probably install them this weekend and see what happens.

---

### Post by phansiizwe on 2007-01-20
I've just done a full update and everything went smoothly (at the moment I was running metacity instead of Beryl...),
when trying to start Beryl, nothing happened. So I guess you will need to use the SVN version of Beryl with the latest updates for now...

---

