---
title: "installing alsa 1.0.11 - help?"
date: 2006-05-25
forum: Installation &amp; Upgrades
---

### Post by pinballkid on 2006-05-25
I've been having trouble with sound on dapper. My sound card is detected with lshw as an 82801G (ICH7 Family) High Definition Audio Controller. From poking around on these forums and the web it seems like this problem may have been fixed in the latest version of alsa - 1.0.11.

I'd like to install it, but I am wary of following the alsa installation instructions as they dont involve building packages (with checkinstall or otherwise) so my package manager will know nothing of it. Also, the source tarballs (driver, library and utils) that come with alsa dont match up with any packages in the ubuntu repositories.

I'd like to install alsa 1.0.11, but I want my package manager to know whats going on. Any ideas on how to do this?

---

### Post by Sutekh on 2006-05-25
The ALSA instructions for your card; [ALSA  Instructions - Intel - HD Audio (ICH7)  ]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+HD-audio+and+modem.&chip=ICH6%2C+ICH6M%2C+ICH7%2C+ESB2&module=hda-intel")can be altered to use checkinstall.

Just follow the instructions up to the make install command and replace it with checkinstall.

So instead of using (for example the drivers)
```
bunzip2 alsa-driver-xxx[FONT=monospace]
[/FONT]tar -xf alsa-driver-xxx
cd alsa-driver-xxx
./configure --with-cards=hda-intel --with-sequencer=yes;make;**make install**
```Use
```
bunzip2 alsa-driver-xxx
tar -xf alsa-driver-xxx
cd alsa-driver-xxx
./configure --with-cards=hda-intel --with-sequencer=yes;make;**checkinstall**
``` Remembering that the bold commands should be run as root, so use sudo before them, ie
```
sudo checkinstall
``` (The ALSA instructions assume that you will follow the whole procedure using root)

What do you mean (specifically) by
[quote=pinballkid]
Also, the source tarballs (driver, library and utils) that come with alsa dont match up with any packages in the ubuntu repositories.[/quote]

---

### Post by pinballkid on 2006-05-26
[QUOTE=Sutekh]
What do you mean (specifically) by: Also, the source tarballs (driver, library and utils) that come with alsa dont match up with any packages in the ubuntu repositories.[/QUOTE]

sorry if I was a bit unclear on this. What I mean is that there are three source tarballs  that the alsa instructions talk about - asla-drivers, alsa-library, and alsa-utils. If I use checkinstall, that will result in three packages of the same names (unless I specifically change those names to someting else). I searched in Synaptic for these packages and cant find them.

So I suppose what I mean is - if I install alsa-driver, alsa-library, alsa-utils, it wont be upgrading existing ubuntu packages, but installing a bunch of new ones as well as whatever is already doing alsa now. Will this conflict with the existing alsa packages that ubuntu has and will it get in the way of automatically updating my system with the new alsa drivers if/when they are included in the distro.

thanks for your time

---

### Post by pinballkid on 2006-05-28
I have tried to install ALSA 1.0.11 from [these instrcutions]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+HD-audio+and+modem.&chip=ICH6%2C+ICH6M%2C+ICH7%2C+ESB2&module=hda-intel"), though I used checkinstall rather than make install. The trouble is that I get this error:

> Unpacking alsa-driver-1.0.11 (from .../alsa-driver-1.0.11_1.0.11-1_i386.deb) ...dpkg: error processing /home/stephen/alsa/alsa-driver-1.0.11/alsa-driver-1.0.11_1.0.11-1_i386.deb (--install):
 trying to overwrite `/lib/modules/2.6.15-23-686/kernel/sound/drivers/mpu401/snd-mpu401.ko', which is also in package linux-image-2.6.15-23-686
dpkg-deb: subprocess paste killed by signal (Broken pipe)

It seems like this is changing something in the kernel, and cant be overridden because the file belongs to another package.

does anyone have any suggestion on how to get around this? Is there any way that I can install this with

---

### Post by Sutekh on 2006-05-28
Hmm.  All I can think of is to install the drivers with a normal make install.  

I don't really know how it works, but I believe what you are doing by make'ing the ALSA drivers is compiling a kernel module, which is inserted into the kernel after being built (modprobe snd[FONT=monospace]-c[/FONT]ard-hda-intel).    I'd just use make install.  If you need to update ALSA you will just have to it manually again, if you need to uninstall just remove the sound modules (rmod  snd-card-hda-intel)

The ALSA utils is more of a package and should checkinstall ok.


Someone might have another way.

---

### Post by ps- on 2006-05-29
If you already have the .deb package, just copy its content over the old driver module. (using midnight commander you can navigate .deb packages for example).

The error message just says that there is a file conflict - thats totally ok, the module is in the linux-kernel package from ubuntu as well as in your new one.

You just need the .ko file to enable the new alsa driver, so copying it over the old one as root should do the trick :) You find it in in /lib/modules/[your-kernel-version]/kernel/sound/pci/[your soundchip]/

---

