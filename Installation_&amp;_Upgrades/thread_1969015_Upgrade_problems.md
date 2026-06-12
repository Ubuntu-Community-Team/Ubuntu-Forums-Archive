---
title: "Upgrade problems"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by No1StoppedMe on 2012-04-29
Tried upgrading and it failed due to lack of space(most likely) in /boot. So I purged the older kernels and the new one that failed to update and now I can't upgrade again because I'm getting this error.

W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)

I've tried running sudo apt-get update and it's not helped. I'm running the 12.04 beta release currently. and the active kernel is "3.2.0-23-generic" I know "3.2.0-24-generic" is available cause thats the one that failed to upgrade. 

Any help would be appreciated. Thanks.

---

### Post by jerrrys on 2012-04-29
Try this:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

---

### Post by No1StoppedMe on 2012-04-29
> **jerrrys said:**
> Try this:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

Tried it. When I went to upgrade "sudo apt-get upgrade" after doing the update I got this again:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

---

### Post by No1StoppedMe on 2012-04-29
> **jerrrys said:**
> Try this:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

Further more when I do the "sudo apt-get update" I get this at the end:

W: Failed to fetch [http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu/dists/precise/main/source/Sources)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

I'm guessing this isn't helping my cause either.

---

### Post by matt_symes on 2012-04-29
Hi

Let's have a look at your sources. Open a terminal and type (or copy and paste)

```
grep -r ^ /etc/apt/sources.list /etc/apt/sources.list.d/*
```Copy and paste (Highlight text>Right click->Copy) and paste not your next post.

Kind regards

---

### Post by No1StoppedMe on 2012-04-29
> **matt_symes said:**
> Hi

Let's have a look at your sources. Open a terminal and type (or copy and paste)

```
grep -r ^ /etc/apt/sources.list /etc/apt/sources.list.d/*
```Copy and paste (Highlight text>Right click->Copy) and paste not your next post.

Kind regards

/etc/apt/sources.list:# 
/etc/apt/sources.list:
/etc/apt/sources.list:# deb cdrom:[Ubuntu-Server 11.10 _Oneiric Ocelot_ - Release amd64 (20111011)]/ dists/oneiric/main/binary-i386/
/etc/apt/sources.list:# deb cdrom:[Ubuntu-Server 11.10 _Oneiric Ocelot_ - Release amd64 (20111011)]/ dists/oneiric/restricted/binary-i386/
/etc/apt/sources.list:# deb cdrom:[Ubuntu-Server 11.10 _Oneiric Ocelot_ - Release amd64 (20111011)]/ oneiric main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:# deb cdrom:[Ubuntu-Server 11.10 _Oneiric Ocelot_ - Release amd64 (20111011)]/ dists/oneiric/main/binary-i386/
/etc/apt/sources.list:# deb cdrom:[Ubuntu-Server 11.10 _Oneiric Ocelot_ - Release amd64 (20111011)]/ dists/oneiric/restricted/binary-i386/
/etc/apt/sources.list:# deb cdrom:[Ubuntu-Server 11.10 _Oneiric Ocelot_ - Release amd64 (20111011)]/ oneiric main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
/etc/apt/sources.list:# newer versions of the distribution.
/etc/apt/sources.list:deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) precise main restricted
/etc/apt/sources.list:deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) precise main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:## Major bug fix updates produced after the final release of the
/etc/apt/sources.list:## distribution.
/etc/apt/sources.list:deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) precise-updates main restricted
/etc/apt/sources.list:deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) precise-updates main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
/etc/apt/sources.list:## team. Also, please note that software in universe WILL NOT receive any
/etc/apt/sources.list:## review or updates from the Ubuntu security team.
/etc/apt/sources.list:deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) precise universe
/etc/apt/sources.list:deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) precise universe
/etc/apt/sources.list:deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) precise-updates universe
/etc/apt/sources.list:deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) precise-updates universe
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
/etc/apt/sources.list:## team, and may not be under a free licence. Please satisfy yourself as to 
/etc/apt/sources.list:## your rights to use the software. Also, please note that software in 
/etc/apt/sources.list:## multiverse WILL NOT receive any review or updates from the Ubuntu
/etc/apt/sources.list:## security team.
/etc/apt/sources.list:deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) precise multiverse
/etc/apt/sources.list:deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) precise multiverse
/etc/apt/sources.list:deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) precise-updates multiverse
/etc/apt/sources.list:deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) precise-updates multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository may not have been tested as
/etc/apt/sources.list:## extensively as that contained in the main release, although it includes
/etc/apt/sources.list:## newer versions of some applications which may provide useful features.
/etc/apt/sources.list:## Also, please note that software in backports WILL NOT receive any review
/etc/apt/sources.list:## or updates from the Ubuntu security team.
/etc/apt/sources.list:deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) precise-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) precise-backports main restricted universe multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-security main restricted
/etc/apt/sources.list:deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-security universe
/etc/apt/sources.list:deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-security multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## Uncomment the following two lines to add software from Canonical's
/etc/apt/sources.list:## 'partner' repository.
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by Canonical and the
/etc/apt/sources.list:## respective vendors as a service to Ubuntu users.
/etc/apt/sources.list:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
/etc/apt/sources.list:deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
/etc/apt/sources.list:
/etc/apt/sources.list:## Uncomment the following two lines to add software from Ubuntu's
/etc/apt/sources.list:## 'extras' repository.
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by third-party
/etc/apt/sources.list:## developers who want to ship their latest software.
/etc/apt/sources.list:deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
/etc/apt/sources.list:deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
/etc/apt/sources.list:deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise universe restricted multiverse main
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security universe main restricted
/etc/apt/sources.list:deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates universe main restricted multiverse
/etc/apt/sources.list:deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-proposed universe main restricted multiverse
/etc/apt/sources.list:deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-backports universe main restricted multiverse
/etc/apt/sources.list.d/danielrichter2007-grub-customizer-precise.list:deb [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) precise main
/etc/apt/sources.list.d/danielrichter2007-grub-customizer-precise.list:deb-src [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) precise main
/etc/apt/sources.list.d/danielrichter2007-grub-customizer-precise.list.save:deb [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) precise main
/etc/apt/sources.list.d/danielrichter2007-grub-customizer-precise.list.save:deb-src [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) precise main
/etc/apt/sources.list.d/mefrio-g-plymouthmanager-oneiric.list:# deb [http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu](http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu) precise main # disabled on upgrade to precise
/etc/apt/sources.list.d/mefrio-g-plymouthmanager-oneiric.list:# deb-src [http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu](http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu) precise main # disabled on upgrade to precise
/etc/apt/sources.list.d/mefrio-g-plymouthmanager-oneiric.list.distUpgrade:deb [http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu](http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu) oneiric main
/etc/apt/sources.list.d/mefrio-g-plymouthmanager-oneiric.list.distUpgrade:deb-src [http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu](http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu) oneiric main
/etc/apt/sources.list.d/mefrio-g-plymouthmanager-oneiric.list.save:# deb [http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu](http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu) precise main # disabled on upgrade to precise
/etc/apt/sources.list.d/mefrio-g-plymouthmanager-oneiric.list.save:# deb-src [http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu](http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu) precise main # disabled on upgrade to precise
/etc/apt/sources.list.d/mefrio-g-plymouthmanager-precise.list:deb [http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu](http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu) precise main
/etc/apt/sources.list.d/mefrio-g-plymouthmanager-precise.list:deb-src [http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu](http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu) precise main
/etc/apt/sources.list.d/mefrio-g-plymouthmanager-precise.list.save:deb [http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu](http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu) precise main
/etc/apt/sources.list.d/mefrio-g-plymouthmanager-precise.list.save:deb-src [http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu](http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu) precise main
/etc/apt/sources.list.d/oneiric-partner.list:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner #Added by software-center
/etc/apt/sources.list.d/oneiric-partner.list.distUpgrade:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner #Added by software-center
/etc/apt/sources.list.d/oneiric-partner.list.save:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner #Added by software-center

---

### Post by matt_symes on 2012-04-29
Hi

Open a terminal and type (the stars at the end are important)

```
sudo rm /etc/apt/sources.list.d/oneiric-partner.list*
```

Enter your password. It will not be echoed to the screen

```
sudo rm /etc/apt/sources.list.d/mefrio-g-plymouthmanager-precise.list*
```

Then follow the steps in post #2 by jerrrys again.

After that

```
sudo apt-get update
```

Kind regards

---

### Post by No1StoppedMe on 2012-04-29
> **matt_symes said:**
> Hi

Open a terminal and type (the stars at the end are important)

```
sudo rm /etc/apt/sources.list.d/oneiric-partner.list*
```Enter your password. It will not be echoed to the screen

```
sudo rm /etc/apt/sources.list.d/mefrio-g-plymouthmanager-precise.list*
```Then follow the steps in post #2 by jerrrys again.

After that

```
sudo apt-get update
```Kind regards

Thanks guys. This has gotten rid of the duplicates and the missing files. Now on to the next problem. Ubuntu thinks it's already upgraded to the new version but I'm still running the "3.2.0-23" kernel. Any ideas why I'm getting this when I try to run "sudo apt-get dist-upgrade"?:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by matt_symes on 2012-04-29
Hi

Can you post the output of these commands

```
uname -a
```

```
dpkg -l linux-image
```

That is a small L after dpkg.

```
dpkg -l linux-image-generic-pae
```

Kind regards

---

### Post by No1StoppedMe on 2012-04-29
> **matt_symes said:**
> Hi

Can you post the output of these commands

```
uname -a
``````
dpkg -l linux-image
```That is a small L after dpkg.

```
dpkg -l linux-image-generic-pae
```Kind regards

uname -a
Linux chrisdesktop 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

dpkg -l linux-image
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  linux-image    <none>         (no description available)

dpkg -l linux-image-generic-pae
No packages found matching linux-image-generic-pae.

---

### Post by matt_symes on 2012-04-29
Hi

```
matthew@matthew-Aspire-7540 ~ % apt-cache show linux-image | grep -iA2 description-en
Description-en: Generic Linux kernel image.
 This package will always depend on the latest generic Linux kernel image
 available.
matthew@matthew-Aspire-7540 ~ %
```I think you need it installed to get the updated kernel. Try this

```
sudo apt-get install linux-image
``````
sudo apt-get update
``````
sudo apt-get dist-upgrade
```

That should then, hopefully, install the new kernel for you when there is an update.

Kind regards

---

### Post by No1StoppedMe on 2012-04-29
> **matt_symes said:**
> Hi

```
matthew@matthew-Aspire-7540 ~ % apt-cache show linux-image | grep -iA2 description-en
Description-en: Generic Linux kernel image.
 This package will always depend on the latest generic Linux kernel image
 available.
matthew@matthew-Aspire-7540 ~ %
```I think you need it installed to get the updated kernel. Try this

```
sudo apt-get install linux-image
``````
sudo apt-get update
``````
sudo apt-get dist-upgrade
```That should then, hopefully, install the new kernel for you when there is an update.

Kind regards

Thank You! That got the kernel installed. Now I'm having troubles with nVidia x Server. My resolution changed so when I went in to x server to fix it I got this message:

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

So I ran it and this is what I got:

chris@chrisdesktop:~$ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

ERROR: Unable to write to directory '/etc/X11'.



Any ideas?

---

### Post by matt_symes on 2012-04-29
Hi

Wow. You are having problems :)

From the terminal
```

sudo  nvidia-xconfig
```

Kind regards

---

### Post by No1StoppedMe on 2012-04-29
> **matt_symes said:**
> Hi

Wow. You are having problems :)

From the terminal
```

sudo  nvidia-xconfig
```Kind regards

LOL I know right? I haven't had this many issues since I switched to Ubuntu back in October! I'm still working on why MS Office 2010 won't install in Virtual Box! lol but we won't get into that problem right now since I'm still trouble shooting it. lol Below is what I got when I ran your command and I opened nVidia X Server again after and got the same error that I'm not using the nVidia Driver

This is what your command gave me and below is the nVidia error again:

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

Is a restart required maybe?

---

### Post by matt_symes on 2012-04-29
Hi

Yes. A restart be required....

....Or you can restart the X server as suggested from a console but i would just restart.

You can post the output of the file if you like but i am no expert at nVidia.

```
cat /etc/X11/xorg.conf
```

> I'm still working on why MS Office 2010 won't install in Virtual Box!

Is there anything wrong with libre office ?

Kind regards

---

### Post by No1StoppedMe on 2012-04-29
I'm gonna start a new thread for this issue. Restart didn't help. Thanks a million for you help Matt! Do you know of a good utility to expand the /boot partion without losing all your data?

---

### Post by No1StoppedMe on 2012-04-29
```
cat /etc/X11/xorg.conf
```

Is there anything wrong with libre office ?

Kind regards[/QUOTE]

Nothing wrong with it. Just my job requires me to use MS Office and there are some features in MS Office that don't convert properly to Libre Office so I'm using MS to avoid compatibility issues. It's just a pain running a dual boot environment so I went the route of Virtual Box so I could have both environments open at the same time. :)

---

### Post by matt_symes on 2012-04-29
Hi

> **No1StoppedMe said:**
> I'm gonna start a new thread for this issue. Restart didn't help.

That's probably a good idea. I use ATI cards.
```

matthew@matthew-Aspire-7540 ~ % lspci | grep -i vga
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series]
matthew@matthew-Aspire-7540 ~ % 
```Post your xorg config file in that thread.

>  Thanks a million for you help Matt!You're welcome :)

> Do you know of a good utility to expand the /boot partion without losing all your data?I just use gparted to resizing partitions but i highly recommend backing up your hard drive first.

Kind regards

---

