---
title: "can't properly install nvidia drivers version 190"
date: 2009-08-31
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by orlox on 2009-08-31
Hi. Im trying to get the 190 version of the nvidia drivers installed in karmic, using the vdpau ppa. Actually, I was using t for some days, but after a recent update (which was a partial upgrade through update-manager), the drivers where uninstalled.

Now, if try to manually install this drivers (hardware controllers doesnt work...) by installing the nvidia-glx-190 package, it says it cant install the dependency nvidia-190-libvdpau. And if I try to specifically install the nvidia-190-libvdpau package, Synaptic says that it needs to uninstall every single kde app I have!

---

### Post by FrancoNero on 2009-08-31
don't even see a 190 driver series on nvidia.com, what are you talking about?

---

### Post by zenarcher on 2009-08-31
Maybe this:

[http://www.nvidia.com/object/linux_display_amd64_190.18.html](http://www.nvidia.com/object/linux_display_amd64_190.18.html)

Or possibly this:

[https://launchpad.net/~nvidia-vdpau/+archive/ppa/+build/1146849](https://launchpad.net/~nvidia-vdpau/+archive/ppa/+build/1146849)

Cheers,
zenarcher

---

### Post by orlox on 2009-08-31
> **zenarcher said:**
> Maybe this:

[http://www.nvidia.com/object/linux_display_amd64_190.18.html](http://www.nvidia.com/object/linux_display_amd64_190.18.html)

Or possibly this:

[https://launchpad.net/~nvidia-vdpau/+archive/ppa/+build/1146849](https://launchpad.net/~nvidia-vdpau/+archive/ppa/+build/1146849)

Cheers,
zenarcher

yup, those precisely

---

### Post by bl33d on 2009-08-31
have you tried installing them manually with the vanilla nvidia driver? although when karmic updates yuo might need to reinstall them :3

---

### Post by orlox on 2009-08-31
> **bl33d said:**
> have you tried installing them manually with the vanilla nvidia driver? although when karmic updates yuo might need to reinstall them :3

I know I could do that (ot would probably work since I wouldnt have package dependency issues like I have now), but since they're beta drivers, I'd like to have them managed through a ppa.

However, I still cant find what dependencies cause this problem. Also, If I try to remove nvidia-185-libvdpau, the package manager tells me it needs to wipe clean my pc from kde apps. What could possibly make the kde core depend on this propietary drivers???

---

### Post by bl33d on 2009-08-31
> **orlox said:**
> I know I could do that (ot would probably work since I wouldnt have package dependency issues like I have now), but since they're beta drivers, I'd like to have them managed through a ppa.

However, I still cant find what dependencies cause this problem. Also, If I try to remove nvidia-185-libvdpau, the package manager tells me it needs to wipe clean my pc from kde apps. What could possibly make the kde core depend on this propietary drivers???

you can easily uninstall them with 

```
sudo nvidia-installer --uninstall
```

ifsomething goes wrong

---

### Post by orlox on 2009-08-31
> **bl33d said:**
> you can easily uninstall them with 

```
sudo nvidia-installer --uninstall
```

ifsomething goes wrong

Yes, im aware of that. But considering nvidia developers have a ppa with the drivers, id prefer to solve this issue instead of using the installer. Also, I'd like to understand what could posibly cause this dependencies issue.

---

### Post by bl33d on 2009-08-31
> **orlox said:**
> Yes, im aware of that. But considering nvidia developers have a ppa with the drivers, id prefer to solve this issue instead of using the installer. Also, I'd like to understand what could posibly cause this dependencies issue.

nvidia has a ppa? 0_0

---

### Post by orlox on 2009-08-31
Actually, the developers of nvidia vdpau have one, but they provide all versions of the nvidia drivers also (I believe they also provide a compiled mplayer with vdpau support).

This is the ppa:

[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

---

### Post by dinxter on 2009-08-31
strange, using the ppa at [https://launchpad.net/~nvidia-vdpau/...+build/1146849]("https://launchpad.net/%7Envidia-vdpau/+archive/ppa/+build/1146849") i can install all the 190 packages on amd64, only the older nvidia packages are removed. kdebase kde-workspace and so on are installed and arent affected, along with all the kde apps they pulled in

---

### Post by dinxter on 2009-08-31
looking at the debs, the conflicts and so on look as they should be too

---

### Post by orlox on 2009-08-31
> **dinxter said:**
> strange, using the ppa at [https://launchpad.net/~nvidia-vdpau/...+build/1146849]("https://launchpad.net/%7Envidia-vdpau/+archive/ppa/+build/1146849") i can install all the 190 packages on amd64, only the older nvidia packages are removed. kdebase kde-workspace and so on are installed and arent affected, along with all the kde apps they pulled in

mmm, that's weird...Wonder what's the difference that causes me this trouble...

---

### Post by bl33d on 2009-08-31
why do u need 190? 185.18.36 works ok :P

---

### Post by orlox on 2009-08-31
> **bl33d said:**
> why do u need 190? 185.18.36 works ok :P

I dont need it, but that certainly is not enough reason not to have them!
In that same spirit, I don't need karmic, since jaunty works perfectly fine on my machine, yet, I'm using karmic as my only OS since alpha 2.

---

### Post by bl33d on 2009-08-31
> **orlox said:**
> I dont need it, but that certainly is not enough reason not to have them!
In that same spirit, I don't need karmic, since jaunty works perfectly fine on my machine, yet, I'm using karmic as my only OS since alpha 2.

lol :P

---

### Post by orlox on 2009-08-31
Well, closing up a little bit on the dependencies...

It seems the conflict has something to do with the libxine1 package. I simply installed the 190 drivers, and accepted all the uninstalling. 

Afterwards, I tried installing the only kde program I use, kile, but triyng to install it removes the 190 drivers, and besides other stuff, tries to install libxine1. Now, I tried to install libxine1, and guess what? It tries to remove my 190 drivers. What am I missing here :confused:???

---

### Post by lithorus on 2009-09-01
I use this ppa and have no problems with all the latest packages :
> deb [http://ppa.launchpad.net/thefirstm/ppa/ubuntu](http://ppa.launchpad.net/thefirstm/ppa/ubuntu) jaunty main
(yes, it's supposed to say jaunty)

---

### Post by Darkshade on 2009-09-01
[QUOTE=https://launchpad.net/~nvidia-vdpau/+archive/ppa]Xine-vdpau is a replacement for Xine which contains vdpau support. Most of the frontends for Xine should use the vdpau driver and codecs automatically, but Totem-Xine needs a bit of a push. To use with Totem-Xine, go to ~/.config/totem and open xine_config. change #video.driver:auto to video.driver:vdpau.[/QUOTE]

Maybe the different versions of Xine conflict somehow?

---

### Post by magor on 2009-09-01
[orlox]("http://ubuntuforums.org/member.php?u=64859") is not alone. I am having the exact same problem. Its either nvidia 190 or KDE, not both.

---

### Post by orlox on 2009-09-01
I've cracked down the dependency issue I think. However, I still don't get why some people arent be affected by this...
[LIST]
[*]nvidia-glx-190 replaces nvidia-glx-185
[*]nvidia-185-libvdpau depends on nvidia-glx-185
[*]libxine1-bin depends on nvidia-185-libvdpau
[*]libxine1-x depends on libxine1-bin
[*]libxine1 depends on libxine1-x
[*]phonon-backed-xine depens on libxine1
[*]kdebase-runtime depends on phonon-backed-xine
[/LIST]
So there it is! installing nvidia-glx-190 from the vdpau ppa should inevitably get kdebase-runtime uninstalled! I'll try to see if I can get any further than this...

---

### Post by orlox on 2009-09-01
Just contacted Brandon Snider, the man in charge of the vdpau ppa (he answered a mail in less than a minute :o)

This is what he mentioned:

> That's exactly right because I built the libxine packages against the 185 driver, which Nvidia considers to be the current stable driver.You'll have to do some trickery if you want to use the 190 driver with KDE.

Soooooo, it seems kde is incompatible with this build of the 190 driver...bummer...

---

### Post by dabl on 2009-09-02
I'm not sure whether there's a 4-leaf clover under my desk, or what -- I just came across this thread and kind of broke out in a sweat.

I don't know anything about "vdpau" -- apparently it is not important to my use of the computer. However, I'm running Kubuntu 9.10 64-bit, and using the Beta nVidia 190.18.03 driver from here:

[http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

I have a GTX 260 that displays on a big Samsung 1100 CRT.

I ran updates last night, which was pretty major (231 updated packages and 5 new ones) and included the new 2.6.28-9 kernel, and then I booted the new kernel and reinstalled the nVidia driver like I always do, and it works just fine, along with Compiz and Emerald.  plasma-desktop still seems a little crash-prone (possibly caused by Compiz & Emerald, rather than KDM), although I haven't been running on the new kernel long enough to say whether it is better, worse, or about the same.  So, I guess I was happy being oblivious to the problem reported on this thread.  :(

---

### Post by orlox on 2009-09-02
dabl, you don't have any problems since you're directly using the nvidia installer, wich does not provide the libxine packages that dont allow me to install from the ppa.

Im also interested on this xine packages, cause they are compiled with vdpau support, and I dont think there's an easy way to get them without this ppa.

---

### Post by dlenmn on 2009-09-07
I was having the same problem with trying to install the 190 drivers. Thanks for finding the cause of it. Did Brandon Snider give any type of time frame for when we might expect 190 support?

---

### Post by orlox on 2009-09-07
He didn't mentioned that directly, but from his words, Im guessing he might package it when 190 becomes officially stable...

---

### Post by philpem on 2009-09-08
I had a similar issue this evening with my jaunty install -- I installed the 190 driver set from the vdpau PPA so I could run the Cuda2.3 SDK, and Apt/Synaptic/et al kept wanting to downgrade my nVidia drivers back to 185 so they could install the VDPAU version of libxine1.

I've worked around this by just installing the nVidia drivers from the PPA:

```
$ cat /etc/apt/preferences
Package: nvidia-190-*
Pin: release o=LP-PPA-nvidia-vdpau
Pin-Priority: 600

Package: nvidia-glx-190
Pin: release o=LP-PPA-nvidia-vdpau
Pin-Priority: 600

Package: nvidia-settings-190
Pin: release o=LP-PPA-nvidia-vdpau
Pin-Priority: 600

Package: *
Pin: release o=LP-PPA-nvidia-vdpau
Pin-Priority: -1000

```

After this, run:
```
$ sudo apt-get clean
$ sudo apt-get update
$ sudo apt-get dist-upgrade
```
(APT should tell you that nothing needs upgrading)

What this does is "pins" the packages from the nvidia-vdpau PPA. The first three lines make sure that the nvidia-190-whatever, GLX and settings panel packages take priority, and the last pinning stops any other packages from the vdpau repository from being installed.

The catch is that when (if?) the VDPAU-capable Xine is released, you'll have to add the relevant pinnings to /etc/apt/preferences...

---

### Post by ubongo2008 on 2009-09-10
The exact problem is: 
kde-runtime -> libxine1 -> libxine-x -> libxine-bin -> f*u*c*k*e*d  coz libxine-bin is build against nvidia-185-libvdpau 

and no the solution from philpem did not help ](*,)

so the problem isn*t the nvidia-driver it is libxine-bin .... at least for my depency graph

OFFTOPIC: Does anyone get sound with xine and libvdpau support when using DVB-S? I get sound drop offs all the time?

i also don't get why libxine1 isn't just an suggested or recommended package of kde-runtime

maybe someone can suggest an solution or post an bugreport to kde-runtime package maintainer may be that would be the easiest solution but i will go to bed now ...

for now i'll try the binary installer from nvidia ... hope that will help


maybe someone can suggest an solution or post an bugreport to kde-runtime package maintainer may be that would be the easiest solution but i will go to bed now ...

---

### Post by fooman on 2009-09-18
> **lithorus said:**
> I use this ppa and have no problems with all the latest packages :

(yes, it's supposed to say jaunty)

[http://ubuntuforums.org/showpost.php?p=7879187&postcount=18](http://ubuntuforums.org/showpost.php?p=7879187&postcount=18)

hey that worked for me using jaunty!  :)

i had been trying for weeks getting the 190.* drivers installed....kept running into that wall with the kde and xine stuff.  added the repo from the link above and #'ed out the other nvida repos....bingo,  the only kde package that was uninstalled in the process was kdelive,  which doesn't affect anything that i need.  it installed some other xine & kde packages and right now all seems good.  vdpau is working properly with both xine and mplayer.

looks like there are karmic packages there as well.

thanks lithorus.

---

