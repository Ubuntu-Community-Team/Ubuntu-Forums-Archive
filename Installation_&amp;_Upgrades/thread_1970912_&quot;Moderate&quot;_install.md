---
title: "&quot;Moderate&quot; install"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by raptir on 2012-05-01
I'm planning on running Kubuntu on my new laptop primarily for the Plasma Desktop and Kwin. However, I'm not a fan of many of the KDE applications (I prefer Firefox to rekonq... I've had issues with getting my gmail syncing with Kmail compared to Thunderbird...).

I read about performing a minimal install, which starts you off with a command line and you build up from there. I am comfortable with that, but I want to make sure that I'm getting everything I need installed. Apart from installing kde-plasma-desktop and whatever desktop applications I want, what other software do I need to get an optimally functioning system? For example, to get full power control (both CPU scaling, which I am assuming is built into the kernel, as well as getting Suspend to work), Bluetooth support, printing support, auto-mount for USB file systems, etc... 

**Basically, how do I install everything *buntu except for the desktop environment itself from a minimal install?**

---

### Post by raptir on 2012-05-04
Would I possibly be better off doing a full install and removing the programs I don't want? Or is there any main package I can install that will install all the "extra essentials"?

---

### Post by 909-1 on 2012-05-05
You can install a bare minimum linux with no desktop environment using this: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD).

Just burn the mini.iso to CD or USB. You'll need a wired connection since all packages are installed directly from the repositories. It will boot into the command line. From there you can install whatever you want.

This should get you started with a basic KDE install:

```
sudo apt-get install kde-plasma-desktop xorg
```Packages for Precise: [http://packages.ubuntu.com/precise/](http://packages.ubuntu.com/precise/)
Packages for Precise > KDE: [http://packages.ubuntu.com/precise/kde/](http://packages.ubuntu.com/precise/kde/)

You can pick and choose only the packages you need without the "extras". Doing similiar steps for Gnome 32bit, my RAM use on booting is 140MB.

---

### Post by raptir on 2012-05-06
Thanks for the input. But what I'm really looking for is what extra packages do I need to install to get an optimal system? Specifically any of the "behind the scenes" operations like power management. 

Basically, after I do a minimal install and install plasma, is there anything else I need that might not be readily apparent?

Edit: Put another way, is Kubuntu just the minimal install plus the Kubuntu-desktop package? Or is there anything else I need to look at?

---

### Post by raptir on 2012-05-10
Does anyone have any input? Specifically, is Kubuntu just a minimal ubuntu install plus kubuntu-desktop, or are there other packages I need to look at?

---

### Post by kc1di on 2012-05-10
if I'm not mistaken Kubuntu uses Ubuntu as a base and strips most the the gtk libraries and replaces them with qt equivalents then the plasma desktop is added.

---

### Post by kc1di on 2012-05-10
If I were doing it I'd do the full kubuntu install providing I had plenty of disk space.  Then just add thunderbird and and other programs I needed.

---

### Post by daisyflower on 2012-05-10
Would a laptop installation of Kubuntu be the same as the desktop installation?  Or is it more similar to a netbook installation?

---

### Post by sudodus on 2012-05-10
> **kc1di said:**
> If I were doing it I'd do the full kubuntu install providing I had plenty of disk space.  Then just add thunderbird and and other programs I needed.
+1
I am testing 12.04 right now with an installation of

- 'vanilla' Ubuntu
- kubuntu-desktop
- lubuntu-desktop
- xubuntu-desktop

and it works. Packages that are not activated take space on the HDD, but that is usually not a problem.

So install the flavour you like the best, and add the packages you want! If necessary, remove the packages you don't want.

---

### Post by sudodus on 2012-05-10
> **daisyflower said:**
> Would a laptop installation of Kubuntu be the same as the desktop installation?  Or is it more similar to a netbook installation? I think it is the same. But if you select to install some proprietary drivers (to fit the graphics chip) the installations will differ. And of course, you can select 32- or 64-bit versions depending of the cpu.

---

### Post by kc1di on 2012-05-10
with the merger of Unity into the main distro there is no more netbook spin.
Cheers!

---

### Post by SeijiSensei on 2012-05-10
Just install Kubuntu and add the packages you want afterwards.  Even if you install a GTK+ application that pulls in all the dependent libraries, you should still have lots of available disk storage on a modern machine.  The only situation I can see that might be problematic is if the computer uses a solid-state disk that has only 16-32 GB of storage.  On my Kubuntu 12.04 machine with Firefox, Thunderbird, GIMP, and synaptic all installed, I'm still using only 5-6 GB for the system.  /lib and /usr represent about 4.5 GB of that.

---

### Post by raptir on 2012-05-10
Well, I don't care about disk space, but I'm more worried about having things I don't need running in the background. Some things, like Akonadi, are easy to find and remove, but I'm assuming there are some things I wouldn't notice immediately.

---

### Post by sudodus on 2012-05-10
You can compare the cpu and memory usage between a clean live session and the installed system. Htop is a good tool for that:
```
sudo apt-get install htop
```

---

### Post by raptir on 2012-05-10
Alright, so I ran into some trouble with a minimal install, so I decided to do a live install and go from there. There's actually not that much I want to remove (maybe some stuff I wouldn't have installed, but it's trivial), but there's one issue I'm running into. I can't remove or disable akonaditray. If I try to remove it, it tries to remove half my system. Any way to disable it completely? A few things I've googled haven't worked.

---

### Post by kc1di on 2012-05-11
here's a page that discribes Akonadi and why it's so invasive in a 
KDE 3 system it would be very hard to seperate it from KDE. if you do not want it I'd change to Ubuntu. Just My honest opinion.

[http://community.kde.org/KDE_PIM/Akonadi]("http://community.kde.org/KDE_PIM/Akonadi")

[http://en.wikipedia.org/wiki/Akonadi]("http://en.wikipedia.org/wiki/Akonadi")
and this one tells you how to keep it from starting :

[http://mschlander.wordpress.com/2011/08/18/disable-akonadi-in-kde-sc-4-7/]("http://mschlander.wordpress.com/2011/08/18/disable-akonadi-in-kde-sc-4-7/")

---

### Post by raptir on 2012-05-11
Alright, thank you. I guess I didn't realize just how integrated everything was with KDE. My main reason for choosing it was that kwin seems to perform much better than Compiz for me (less CPU usage, better battery life). I guess I'll look at Xubuntu.

---

### Post by SeijiSensei on 2012-05-11
You can turn off Akonadi by right-clicking the Akonaditray app in the System Tray, choosing Configure, then choosing the server settings tab and clicking Stop.  It takes a few seconds to shut down.  You'll see a notification that it's disabled when it's done.

There's very little that cannot be configured the way you want in KDE.

---

