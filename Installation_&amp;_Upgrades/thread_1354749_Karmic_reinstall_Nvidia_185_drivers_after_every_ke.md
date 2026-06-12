---
title: "Karmic: reinstall Nvidia 185 drivers after every kernel update?"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by godz on 2009-12-14
Hi,
After every new kernel update (two for the moment) the system always boots in low graphics mode and I need to reinstall the Nvidia 185 related packages from Synaptic. nvidia-xconfig & restart is not enough, every Nvidia 185 related package needs to be reinstalled in order not to end up in low graphics mode. Should it really be necessary to do like this for every kernel update?

64-bit Karmic
GeForce GT 220

Thanks!

---

### Post by audiomick on 2009-12-14
I dont have to do that, at least not for running updates. I am pretty sure I have only ever had to re-install it after a fresh install.

---

### Post by ratcheer on 2009-12-14
I have to reinstall the nVidia driver after each kernel update. It has become routine, for me.

Tim

---

### Post by presence1960 on 2009-12-14
Hmmm. I just upgraded to 2.6.31-17. Not only then but I have never had to do so with the Nvidia driver. I always click the details at the bottom when the packages are downloading so I can watch what is going on in terminal during installation. It always shows the Nvidia driver being installed & configured along with the kernel. Maybe next time you upgrade a kernel click details and watch the terminal output for the Nvidia driver installation. Maybe it will show an error message which can give you a clue as to why the Nvidia driver did not install during the kernel upgrade.

---

### Post by mobrien118 on 2010-01-13
> **ratcheer said:**
> I have to reinstall the nVidia driver after each kernel update. It has become routine, for me.

If you are just installing the drivers from the nVidia website, you will have this problem.

If you install them from the Ubuntu repos (using "System"-->"Administration"-->"Hardware Drivers") you won't have this problem because dkms will rebuild modules whenever you get a new kernel.

If these drivers aren't new enough for you, you can install the newest 185, 190 and 195 versions of the drivers from the ppa. There are instructions all over the place on how to use ppas. Here is the URL for the nVidia ppa:

[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

Hope this helps.

--mobrien118

---

### Post by svenni on 2010-02-07
I had the same problem and figured that linux-headers-generic was not marked as installed in Synaptic. This package always provides the newest headers, which are needed by the nvidia driver after a kernel upgrade. 

After marking linux-headers-generic as installed, the nvidia-glx-185 drivers update themselves to the newest kernel version - as they are supposed to.

---

### Post by ratcheer on 2010-02-07
> **svenni said:**
> I had the same problem and figured that linux-headers-generic was not marked as installed in Synaptic. This package always provides the newest headers, which are needed by the nvidia driver after a kernel upgrade. 

After marking linux-headers-generic as installed, the nvidia-glx-185 drivers update themselves to the newest kernel version - as they are supposed to.

Great thinking. I am going to try that. I never installed the headers because I don't do any system programming. For some reason, I thought they were only needed by active developers.

Tim

---

### Post by yazmonium on 2010-02-08
> If these drivers aren't new enough for you, you can install the newest  185, 190 and 195 versions of the drivers from the ppa. There are instructions all over the place  on how to use ppas. Here is the URL for the nVidia ppa:

[https://launchpad.net/~nvidia-vdpau/+archive/ppa]("https://launchpad.net/%7Envidia-vdpau/+archive/ppa")This sounds like the right fix, but I've installed firefox and vlc with ppa repositories and both programs crash and are a little buggy.  Are you sure this archive isn't buggy as well?

---

### Post by m.letcher on 2010-02-23
I have had problems with each kernel upgrade getting the nvidia drivers to actually install. In fact, I've only had a short period of success when I got the native Nvidia driver to install back on a Hardy install. 

Since the Koala upgrade, nothing for nvidia installs so I'd appreciate any help.

Jockey doesn't even identify the 8800_GT card and suggest proprietary drivers. I've tried Symantec for 185, 190 and 195 drivers.

The latest Nvidia native driver doesn't install either with missing libnvidia-cfg.so.*** and libglx.so.xserver-xorg-core files 

My preference would be to get the 190 driver from ppa going though the 185 would be fine as well. 

Invariably, I get a (EE) the the driver can't initialize the card and get thrown back to VESA low res. I've pointed it at the correct PCI bus ID though it finds it on its own just fine. There's only one card and its at 1:0:0. There are two LCDs attached, though I tried installs with just one connected as I found a youtube suggesting that 2 can be troublesome until a nvidia driver gets installed.

I can and have sent full logs for individual installs if I can find anyone patient enough to walk through an install of your choice.

---

### Post by m.letcher on 2010-03-04
Just following up in absence of advice. I'm still looking for a solution. My next step will following instructions from here:

[http://ubuntuforums.org/archive/index.php/t-1230941.html](http://ubuntuforums.org/archive/index.php/t-1230941.html)

The relevant info appears to be:
If you can't find one of these files that are pointing to the wrong version, or sysinfo tells you you have a version other than 180.44 installed your best bet would be to remove the drivers entirely and reinstall them. To do this, type "apt-get remove --purge nvidia-180-kernel-source nvidia-180-libvdpau nvidia-180-modaliases nvidia-common nvidia-glx-180 nvidia-settings" at a commandline, then the same thing again but with no --purge and with remove replaced by install. You may need to close down X and log in at the black screen before doing this.

So, later this week when I get a chance I'll give it a try. 
This is clearly an area where "Ubuntu just (doesn't) works."

Reminds me of playing with mode lines in Slackware to get a friends linux running more than 15 yrs back.

---

### Post by godz on 2010-03-04
Noticed during recent kernel upgrade:

 *  nvidia (190.42)...
nvidia (190.42): Unable to locate /var/lib/dkms/nvidia/190.42/source/dkms.conf
	DKMS tree must be manually fixed.
   ...fail!


I have installed the drivers from Ubuntu repos, so that is not the problem. But I am using 185 and not 190.42. The above directory does exist, but is empty. Must be some sort of version mix-up?

---

### Post by godz on 2010-08-22
Noticed the same problem today when I upgraded to new kernel.

 *  nvidia (190.42)...
nvidia (190.42): Unable to locate /var/lib/dkms/nvidia/190.42/source/dkms.conf
	DKMS tree must be manually fixed.
   ...fail!

I remember half a year ago I upgraded for some reason to 190.42 an then later on I removed it (for some reason I don't remember) and went back to 185. So this link is invalid: /var/lib/dkms/nvidia/190.42/source -> /usr/src/nvidia-190.42

And this is the valid /var/lib/dkms/nvidia/185.18.36/source -> /usr/src/nvidia-185.18.36 with the dkms.conf file. Could this problem be connected to "rolling back" to old nvidia driver version doesn't work? During upgrade of kerenel ubuntu thinks the latest is the one to use and where is that stated?

Ok, later on today I will go for network upgrade to 10.04, hopefully this problem is solved.

---

