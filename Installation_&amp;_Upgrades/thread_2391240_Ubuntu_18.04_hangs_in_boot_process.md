---
title: "Ubuntu 18.04 hangs in boot process"
date: 2018-05-07
forum: Installation &amp; Upgrades
---

### Post by rj20112 on 2018-05-07
I have twice tried to install 18.04:  once by upgrading from 17.10, and once by a clean install in a new partition.  In both cases, the same thing happens: when rebooting after install, I get cleanly to the multi-boot menu in grub (Windows 10, 17.10, and 18.04).  When I select 18.04, the screen momentarily shows the Ubuntu logo with progress dots below, then goes blank and never gets further.  Its hang-up appears to be display related, because the display ping-pongs between searching for a signal and trying to display a signal.  Tried booting through advanced options/recovery, chose fixing package problems, then continued to boot and ended up in a low-resolution display (monitor is 4k.)  Only one resolution was available.  Thought the problem must be driver related, found and installed the recommended nVidia driver...no change.  Please help if you can.  Not a noob (been using Ubuntu since 8.04), but not an expert, either.  Would really appreciate any help.     System is      Intel i7-4700 quad-core,                             16GB Memory,                              nVidia GeForce GT 720,                              Samsung 28" 4k Monitor. Thanks in advance.

---

### Post by oldfred on 2018-05-07
Which nVidia driver did you install?

I have GT620 and 390.xx driver and it just works.
fred@bionic-z97:~$ dkms status
nvidia, 390.48, 4.15.0-20-generic, x86_64: installed
fred@bionic-z97:~$ sudo lshw -c display

 Fermi based should use 390.xx not newer
[https://nvidia.custhelp.com/app/answers/detail/a_id/4656/~/list-of-fermi-series-geforce-gpus](https://nvidia.custhelp.com/app/answers/detail/a_id/4656/~/list-of-fermi-series-geforce-gpus)

---

### Post by rj20112 on 2018-05-08
I believe it was the 390.xx driver, but I didn't write it down and it was a few days ago.  Thanks for replying.  It's really hard to try solutions when it is so convoluted just to get 18.04 functioning.  I will check the next time I have it running.

---

### Post by rj20112 on 2018-05-08
Here is the result:

sam@sam-XPS-8700:~$ dkms status
nvidia, 390.48, 4.15.0-20-generic, x86_64: installed
sam@sam-XPS-8700:~$ sudo lshw -c display
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: GK208 [GeForce GT 720]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f6000000-f6ffffff memory:e8000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:c0000-dffff

So, right now I have only one choice of resolution, which is 1040x768 (4:3), which is miserable.  On top of that, the only way I can boot into Ubuntu 18.04 is to select the second choice in grub for 18.04, go through fixing broken packages, then continuing the boot process...to end up where I am now.  Nothing else works.  Boy, do I need help!!

---

### Post by oldfred on 2018-05-08
Should not have broken packages. Post this:
 cat /etc/apt/sources.list; for X in /etc/apt/sources.list.d/*; do echo; echo; echo "** $X:"; echo; cat $X; done 

If booting with recovery mode, that uses nomodeset which you should not need with nVidia driver installed. Or is system/UEFI set to use internal video.But that may be different video out port, depending on your hardware.

---

### Post by rj20112 on 2018-05-09
Here's the requested info:

sam@sam-XPS-8700:~$ cat /etc/apt/sources.list; for X in /etc/apt/sources.list.d/*; do echo; echo; echo "** $X:"; echo; cat $X; done
# deb cdrom:[Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426)]/ bionic main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse


** /etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-bionic.list:

deb [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) bionic main
# deb-src [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) bionic main
sam@sam-XPS-8700:~$ 





I have to boot through advanced options/package repair because, if I don't, the same hang-up during boot occurs as when I try to boot normally.  Really appreciate your continuing help...hope the above post is helpful.

---

### Post by oldfred on 2018-05-09
Looks like everything is bionic, often issue with packages is some entry that is still the old version.

Not sure about ppa for grub customizer. Do not use that as I prefer to manually change settings. But many have posted it works, just not sure if updated for bionic.

---

### Post by rj20112 on 2018-05-13
Found the problem!  The 4k monitor I am using is capable of 60Hz update for 4k through one of the HDMI ports, which is the one I am using.  Apparently Ubuntu 18.o4 software cannot handle that update rate (Windows 10 hasn't a problem.)  When I switched to the HDMI port which only handles 30Hz update, everything boots fine!  Problem solved.  (Although Ubuntu 18.04 driver does not seem to handle lower resolutions, since 2560x1440 yields a rapidly flashing display..)  Anyway, at least it boots.

---

### Post by echemdaniel on 2018-05-13
Hello @rj20112, I'm having a similar problem on my Inspiron 15 7537, with Intel HD Graphics. Mine displays "[ok] started gnome display manager at...link was shut down"
I'm very new to Linux. Can you offer an assistance?

---

### Post by rj20112 on 2018-05-19
Hello, echemdaniel.  I'm afraid I haven't any suggestions.  I only stumbled onto my solution by trial and error, not by analysis.  There are several differences between 17.10 and 18.04 which have me baffled!  Suggest you start your own thread, since most experts will ignore this one as it is marked "solved."  Good luck.

---

