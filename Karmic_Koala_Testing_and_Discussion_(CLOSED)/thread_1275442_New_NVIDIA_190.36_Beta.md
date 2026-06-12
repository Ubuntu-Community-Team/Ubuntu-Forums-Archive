---
title: "New NVIDIA 190.36 Beta"
date: 2009-09-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-09-25
[http://www.nvnews.net/vbulletin/showthread.php?p=2091962](http://www.nvnews.net/vbulletin/showthread.php?p=2091962)

---

### Post by PRGUY85 on 2009-09-25
> **Nullack said:**
> [http://www.nvnews.net/vbulletin/showthread.php?p=2091962](http://www.nvnews.net/vbulletin/showthread.php?p=2091962)

I have never been one to use Nvidia drivers directly from Nvidia, always use Hardware Drivers app on ubuntu. Yet, currently the driver is not working for me when activating Compiz so perhaps I should give this a try.

One question, will my system get borked on kernel, headers updates? Do I have to build driver every time?

---

### Post by PRGUY85 on 2009-09-25
How can I quit X?

---

### Post by hanzomon4 on 2009-09-25
sudo /etc/init.d/gdm stop

---

### Post by hype on 2009-09-26
Yes you'll have to reinstall after every kernel update, though it's the easiest way to test new nvidia drivers straight away.

And nbtw now, ubuntu uses upstart for starting/stopping services:
you need to use sudo start gdm or sudo stop gdm.

---

### Post by dinxter on 2009-09-26
in the principle of trying to play with the ppa system :)
[https://launchpad.net/~sevenmachines/+archive/nvidia](https://launchpad.net/~sevenmachines/+archive/nvidia)

---

### Post by joey-elijah on 2009-09-26
[quote=hype;8012097]**Yes you'll have to reinstall after every kernel update**, though it's the easiest way to test new nvidia drivers straight away.

There's a thread around here somewhere with instructions to create a simple script that means you don't' need to reinstall every kernel update - it automatically updates itself.

Edit: here it be

**Automatically update manually installed NVidia drivers after kernel updates**
[http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

---

### Post by PRGUY85 on 2009-09-26
I tried to make Compiz work with this new Nvidia driver beta and it still did not work.

---

### Post by hikaricore on 2009-09-26
> **hanzomon4 said:**
> sudo /etc/init.d/gdm stop

Actually as of recent this is no longer the way to do it as you can see here with kdm:

> 
$ sudo /etc/init.d/kdm stop
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service kdm stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop kdm


So the proper way to do it now would be as follows:

> sudo stop kdm

or for gnome

> sudo stop gdm

As for your driver issues you MUST remove ALL nvidia packages before trying to install from the binary installer.
If you do not do this the driver will not work properly and direct rendering will fail.
You're probably better off using a ppa (as was mentioned) or sticking with the installed version unless your hardware requires a newer version.

---

### Post by hanzomon4 on 2009-09-26
right just saw this on my system.. pretty cool

And no you will not need to reinstall the driver thanks to dkms... it rebuilds itself on every update unless something goes wrong, but it shouldn't. Just make sure you have the linux-kernel-header meta package.

---

### Post by hikaricore on 2009-09-26
> **hanzomon4 said:**
> right just saw this on my system.. pretty cool

And no you will not need to reinstall the driver thanks to dkms... it rebuilds itself on every update unless something goes wrong, but it shouldn't. Just make sure you have the linux-kernel-header meta package.

This almost never works with the binary installer.
I've seen it work like twice out of every single time I've ever needed it.  :p

---

### Post by dinxter on 2009-09-27
dkms is a great thing for rebuilding modules for new kernels automatically as required, unfortunately binary modules are great things for being broken, especially for new kernels :)

---

### Post by Nullack on 2009-09-27
> **PRGUY85 said:**
> I tried to make Compiz work with this new Nvidia driver beta and it still did not work.

Compiz wont ever work right until there is proper gpu memory management in the linux platform

---

### Post by FrancoNero on 2009-09-27
190 isn't gonna make it into Karmic anyway, is it?

---

### Post by hanzomon4 on 2009-09-27
> **Nullack said:**
> Compiz wont ever work right until there is proper gpu memory management in the linux platform

Strange... compiz has bee working since breezy unless I've been using something different

---

### Post by PRGUY85 on 2009-09-27
I'm experiencing this bug with all Nvidia drivers, (185,193,96) and throughout all Karmic testing phase:

[https://bugs.launchpad.net/bugs/391461](https://bugs.launchpad.net/bugs/391461)

---

### Post by dino99 on 2009-09-28
after upgrading this driver, grub is unbootable. Installation has put vga=xxx in grub menu, which is deprecated. Need to edit boot line and remove that ****. Curiously, gfxpayload is present.

Am i the only one with that error ?

---

### Post by joey-elijah on 2009-09-28
Installed and using no problem!

---

### Post by Darkshade on 2009-09-29
Just installed it from this ppa: [https://launchpad.net/~sevenmachines/+archive/nvidia](https://launchpad.net/~sevenmachines/+archive/nvidia)

Everything works fine.

---

### Post by Nullack on 2009-09-29
> **dino99 said:**
> after upgrading this driver, grub is unbootable. Installation has put vga=xxx in grub menu, which is deprecated. Need to edit boot line and remove that ****. Curiously, gfxpayload is present.

Am i the only one with that error ?

I never allow the installer to fiddle with my xorg.conf

As for changing the grub menu I highly doubt it would do that - it only asks for permission to edit xorg.conf which I always answer no too.

---

### Post by RAOF on 2009-09-29
> **Nullack said:**
> Compiz wont ever work right until there is proper gpu memory management in the linux platform

The binary nVidia drivers have had one for years; Intel had one in Jaunty, and nouveau & ati have them in Karmic.

If Compiz just isn't working for you, there's a bug somewhere in your driver stack.

---

### Post by Nullack on 2009-09-29
Yes Chris Im aware that NVIDIA wrote gpu memory management into their closed source drivers. However, when I attempted to pursue a series of bug reports with NVIDIA they dismissed them as symptomatic of not having kernel based GPU memory management and marked them as wont be fixed. When I started a thread about it on the NV News forum one of the nvidia linux devs came in and basically said the same thing and that their hands were tied due to platform problems.

Since then Ive given up on desktop composting for Linux.

---

### Post by RAOF on 2009-09-29
That's a pity.  This Intel laptop likes Compiz just fine.

Maybe in a year's time Nouveau will have supported 3D for you :/.  Then we could (in theory) fix your problems. :)

---

### Post by dinxter on 2009-09-29
> **RAOF said:**
> That's a pity.  This Intel laptop likes Compiz just fine.

Maybe in a year's time Nouveau will have supported 3D for you :/.  Then we could (in theory) fix your problems. :)
...and finally my virtual richard stallman will stop complaining :) nouveau is getting there for some though, this is the first release where its a real option, if you're like me and are frightened of compositing and still still use 'classic brew' metacity anyway

---

