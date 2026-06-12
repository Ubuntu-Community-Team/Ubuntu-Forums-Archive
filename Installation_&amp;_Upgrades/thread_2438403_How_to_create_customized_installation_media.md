---
title: "How to create customized installation media?"
date: 2020-03-11
forum: Installation &amp; Upgrades
---

### Post by daryl9 on 2020-03-11
Okay, since I can't [Distribution upgrading from a local repo]("https://ubuntuforums.org/showthread.php?t=2437465") as I would like to, I have decided to explore plan B.  

"Plan B" is to create a customized installation media based on the latest Ubuntu distribution release, e.g. Ubuntu v18.04, add in packages that I need and format it so it's installable on various equipment.  E.g. Dell, HP, Toshiba, Compaq etc... and various models of said manufactures.  


My core focus is the Edubuntu port because it's packed full of educational programs. In order for me to duplicate an Edubuntu installation on v18.04, I will have to manually install several different educational programs and with the number of machines that I work with, and the different makes/models of machines this would be a very daunting task and impossible for me to accomplish. 


Can I take an existing Ubuntu v18.04 installation media, add in the educational packages that I need and then reformat everything back into an installation media so can then install on whatever piece of equipment that I have?  If so, can someone provide me with steps on how to accomplish this?


Thank you.


Daryl

---

### Post by Frogs Hair on 2020-03-11
A web search with your thread title including Linux will yield many tools for creating a custom ISO. Two I know of are  Ubuntu Imager and Pinguy Builder and there are many more, but be sure they are currently supported projects.

---

### Post by daryl9 on 2020-03-11
> **Frogs Hair said:**
> A web search with your thread title including Linux will yield many tools for creating a custom ISO. Two I know of are  Ubuntu Imager and Pinguy Builder and there are many more, but be sure they are currently supported projects.

I searched, but perhaps my search string was specific enough, because I find only how to download an ISO to your machine and put it on a DVD/USB device for installation.  I'll take a look at Ubuntu Imager and Pinguy Builder to see if either one will work for me.

Thank you for your feedback.

Daryl

---

### Post by Impavidus on 2020-03-11
> **daryl9 said:**
> 
My core focus is the Edubuntu port because it's packed full of educational programs. In order for me to duplicate an Edubuntu installation on v18.04, I will have to manually install several different educational programs and with the number of machines that I work with, and the different makes/models of machines this would be a very daunting task and impossible for me to accomplish. 

Why would that be much harder than installing Ubuntu, then installing the package **edubuntu-desktop**? This package is still available for Ubuntu 16.04 and 18.04, even though there no longer is an edubuntu live disk. Or write a script that installs the packages you want, if your wishes are more specific. It shouldn't depend on the details of the hardware.

---

### Post by daryl9 on 2020-03-11
> **Impavidus said:**
> Why would that be much harder than installing Ubuntu, then installing the package **edubuntu-desktop**? This package is still available for Ubuntu 16.04 and 18.04, even though there no longer is an edubuntu live disk. Or write a script that installs the packages you want, if your wishes are more specific. It shouldn't depend on the details of the hardware.

To the best of my knowledge that's just the Gnome desktop that comes bundled in Edubuntu, not the educational packages.  When I install edubuntu, I have to select the packages separately.  They're bundled, preschool, primary, secondary and tertiary, but if I want to install them on a Ubuntu machine, I need to install each and every program individually.  If the bundle is out there, I haven't seen it.

Daryl

---

### Post by tea for one on 2020-03-11
I've experimented with this [https://launchpad.net/cubic](https://launchpad.net/cubic) a few times.

It doesn't have a huge learning curve but you do need to know the exact package names you wish to include/exclude.

Have a search for **cubic iso tutorial** and you should find some tips.

Good luck

---

### Post by oldfred on 2020-03-11
An alternative or Plan C is just to create a script to install all the packages.
Or use dpkg from an existing install to add all the packages you have installed.

My install script has most of the apps that I want, this is just a few of the lines.
```
apt install galculator gparted geany gimp  gramps
apt install procinfo lshw nmap gdisk
apt install lm-sensors make meld ffmpeg hardinfo
apt install gnome-tweak-tool

```

I also use this to extract list of all installed apps and then reinstall all of them in a new install.
My backup includes this also. The dpkg list is a very long text list of all applications and the dependencies. 
If upgrading, you may want to edit it to remove obsolete, old kernels or others. It will not re-install anything already installed.
[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

---

### Post by Impavidus on 2020-03-12
edubuntu-desktop has the four bundles of educational software as recommended dependencies, which have the actual educational software as recommended dependencies. See [https://packages.ubuntu.com/bionic/edubuntu-desktop](https://packages.ubuntu.com/bionic/edubuntu-desktop). Although I'd take oldfred's route and write a script that installs just the applications I wanted.

---

### Post by EuclideanCoffee on 2020-03-12
I use and highly recommend cubic.

During the installation process, you are given a chroot environment that allows you to remove and add packages as well as fully customize your environment with files and startup processes. Highly recommended!

---

### Post by C.S.Cameron on 2020-03-12
Perhaps you could install Ubuntu to a USB and set it up as you wish.
You could either clone that to the Target device or create an image, save the image to a mkusb Persistent flash drive and restore the image to the Target device while booted from the Persistent USB.
The bootable image could also be installed using mkusb or Windows image writer.

---

