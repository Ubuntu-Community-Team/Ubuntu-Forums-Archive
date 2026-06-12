---
title: "Need help upgrading to Studio"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by zorch on 2007-05-21
Hi,
I'm quit new to Ubuntustudio and I have some problems with upgrading to it, can anybody help ?

So  I'm usinf Feisty 7.04 AMD64 and I'm trying to update it over the Studio Repos.

I used the following
sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'
wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update

But after apt-get update I get this error message
Konnte [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release) nicht holen  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)

Can anybody help ? Is it a problem with my AMD64 ? CAn I only use the Repos when I'm running i386 ?

Thank you for helping !

---

### Post by ThinkBuntu on 2007-05-21
What are you trying to upgrade to in particular? All of the software except the new theme and the low-latency kernel is available in the normal Ubuntu repositories. If you can't get into the repos and have bandwidth to spare, download the Ubuntu Studio iso and mount it on your desktop. Then go to the /pool directory. The theme-related files are in the /pool/main/u folder. Keep in mind that you'll need to uninstall the package "ubuntu-desktop", as it conflicts with "ubuntustudio-desktop." 

Here's [a list of all the packages in Ubuntu Studio]("https://wiki.ubuntu.com/UbuntuStudio/PackageList"). I installed the multimedia apps listed over a normal 7.04 install with no problems using normal repositories.

---

### Post by MetalMusicAddict on 2007-05-21
Please pay attention to the stickies. ["Multimedia Production" is NOT the place for general Ubuntu Studio questions.]("http://ubuntuforums.org/showthread.php?t=442299")

---

### Post by ulaz on 2007-05-21
> **ThinkBuntu said:**
> What are you trying to upgrade to in particular? All of the software except the new theme and the low-latency kernel is available in the normal Ubuntu repositories.

I installed the multimedia apps listed over a normal 7.04 install with no problems using normal repositories.

Hi, I'm new too and I haven't installed Ubuntu yet. Can I install the linux-image-lowlatency kernel on Ubuntu (or Kubuntu) 7.04 for AMD64?

---

### Post by supaneko on 2007-06-11
I am curious about the same thing.

If I go into Synaptic and install the "linux-restricted-modules-lowlatency" on an amd64 setup, will I be able to benefit from this? Can it be installed on an amd64 CPU and keep 64-bit support?

---

### Post by zettberlin on 2007-06-18
> **MetalMusicAddict said:**
> Please pay attention to the stickies. ["Multimedia Production" is NOT the place for general Ubuntu Studio questions.]("http://ubuntuforums.org/showthread.php?t=442299")

Thanks for the great advice regarding the structure of the forums - I guess you are about to hammer out any remains of disorder and randomness to be able to start answering questions as soon as the communication-system of Ubuntustudio reaches the state of perfection

:twisted::twisted::twisted:

By the way: thus I dare to try answering the good old userquestion "why do I get this scary error as I try to add the Ubuntustudio-repos to my sources.list":

Looks like the software in the Ubuntustudiorepo is not for amd64 (though kernel-lowlatency from universe is very-well 64bitready - to answer another question).

This of course, is only a assumption based on the errormessage EVERYBODY gets, who tries to add the repo to his/her sources.list on a 64bit-System...

So we all look forward the day when the mighty  devs come down from the olymp to teach us poor feeble  endusers the ways of the ubustudio...

And another by the way:

Dear Metal Music Addict!
 Please do NOT take  this post too personal - you are at least the only one of the Ubustudio-Team that I see here on the forum. Thanks for your efforts and good will - I hope, you'll get some more support from the whole team in the future...

---

### Post by Stinger on 2007-06-19
Quick answer !
Ubuntustudio is i386 only at the moment ( 32 bit ) and only as alternate DVD iso image , no x86 64-bit edition is available at the moment maybe the next release ?

If you have a Feisty x86 64-bit installation you'll need to make a fresh installation if you want ubuntustudio , upgrade is only possible when using Feisty i386 ( 32 bit )

[UpgradingFromFeisty]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromFeisty")

UbuntuStudio Rocks !

:guitar:

---

### Post by zettberlin on 2007-06-19
> **Stinger said:**
> Quick answer !
Ubuntustudio is i386 only at the moment ( 32 bit )


Strange - it just so happens, that I have linux-lowlatency and all the needed Audioapps running as native 64bit-packages in Feisty. But yes, there is a remark, that NO 64bit Install-Disk is available. Hard to understand why, since I got it all up and running (including Ardour 2.0.2 built from scratch) - Is it so hard to pack a Installdisk for 64 or to build the themes for this arch ?

In the repo for ardour 2 and the themes is whatsoever, nothing to be found:

[http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio)

The most important packages for audio and video are available for 64 also, so if you want to make music with Ubuntu Feisty64 you only need to install those and apply the settings described here:

[https://help.ubuntu.com/community/UbuntuStudio/DapperPreparation](https://help.ubuntu.com/community/UbuntuStudio/DapperPreparation)

I did so more or less and everything works fine on my Audio Workstation, so why the hassle if this can be labeled "Ubuntustudio" or not?

---

### Post by supaneko on 2007-06-19
I followed the directions in this thread to have Ubuntu upgraded to Studio. Unfortunately, after the upgrade, when I log in to Ubuntu Studio, the screen goes blank and then displays a blank grey box at the top left corner of the screen. NOTHING happens after this. The box can not be moved, there is no sound, all I can do is move my mouse cursor. I can't seem to figure out how to get past this "grey box of death."

---

### Post by zettberlin on 2007-06-20
> **supaneko said:**
> I followed the directions in this thread to have Ubuntu upgraded to Studio. Unfortunately, after the upgrade, when I log in to Ubuntu Studio, the screen goes blank and then displays a blank grey box at the top left corner of the screen. NOTHING happens after this. The box can not be moved, there is no sound, all I can do is move my mouse cursor. I can't seem to figure out how to get past this "grey box of death."

First guess: 

1.:Try to reinstall the graphics-driver

if this does not help:

2.:log in to a console, become root by sudo bash
and:

dpkg-reconfigure xserver-xorg

second guess:

Try to install and choose a different desktop (such as KDE, XFCE or Fluxbox)

good luck :-)

---

