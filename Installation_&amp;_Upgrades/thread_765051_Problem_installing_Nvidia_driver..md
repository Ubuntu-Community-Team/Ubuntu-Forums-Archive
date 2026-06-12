---
title: "Problem installing Nvidia driver."
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by void_space on 2008-04-24
Hello,

  New to Linux, while searching for a distro, I happen to come across Ubuntu.  Lucky me, a new version just came out so I installed it.

  I am trying to install the Nvidia driver through System/Administration/Hardware Drivers.  Get a listing of "Nvidia accelerated graphics driver" not enabled.  When I click on it, it downloads 1 file.  After which an error pops up saying "E: nvidia-glx: subprocess post-removal script returned error exit status 2". Upon clicking "details" this appears to be the error.

```
Removing nvidia-glx ...
dpkg-divert: error checking /usr/lib32/libGL.so.1: No such file or directory
```

  I can only close this dialog, then a system restart dialog pops up.  Upon restart, nothing changed.

  I am using a 64 bit version of Ubuntu 8.04, with Nvidia 8800GT card.  Any help on this matter would be appreciated.

Thank you.

---

### Post by Ub1476 on 2008-04-24
Make sure that all the sources are checked in System>Administration>Software Sources.  After that, click close and update your system (through update manager or: )

```
sudo apt-get update
sudo apt-get upgrade
```

If you still cannot download the driver for some reason, you can check out [Envy]("http://www.albertomilone.com/nvidia_scripts1.html").

---

### Post by z0mbie on 2008-04-24
.

---

### Post by Peter09 on 2008-04-24
try using envyng for hardy. I'm not sure if it is already installed but it is in the repo's.

Just go to a terminal and type envyng -t

follow the instructions and you should get a working nvidia driver.

PC

---

### Post by Novega on 2008-04-24
Hey guys, I don't mean to hijack this thread but I have a very similar problem...
I've been a windows guy my whole life, I got 8.04 today and I love it! I've just about got everything set up (a lot easier than I thought)...except this pesky nvidia driver. 

I have a 9600GT card but I have a feeling that right now I'm just using a generic driver b/c the image quality isn't that great.  I haven't installed any drivers yet, I tried to use "Envyng" but it doesn't recognize my card...what do I do?

Any help is appreciated, Thanks in advance

---

### Post by Peter09 on 2008-04-24
What exactly does envyng tell you?

PC

---

### Post by Novega on 2008-04-24
I used the terminal method -> sudo envyng -t
I select "Install Nvidia driver" ->1

And I got this...

EnvyNG - Version 1.1.1
Ubuntu Hardy 32bit
EnvyNG ERROR: Envy does not recognise your card as compatible with any version of the driver.this might happen because either your card is not supported by the driver or Envy's hardwaredetection failed. You can try the manual installation at your risk.


How bad can I mess things up if manual detection causes a problem ? or is there another way?

---

### Post by Extraneous on 2008-04-26
There isn't a Linux driver supporting the 9600GT yet, I don't think. It's a pain, as I, like you, installed Ubuntu for the first time yesterday, and have a 9600GT card that I can't get a driver for. 

Don't try the manual install of the latest nVidia driver offered by envy, either. Messes stuff up a fair bit (boots to a fuzzy nVidia logo, have to uninstall through CLI).

---

### Post by buntunub on 2008-04-26
Dont quote me on this, but I am fairly certain that the 9600 can use the same driver as the 8800, since its basically the same chipset, just modified some.

---

### Post by Extraneous on 2008-04-26
Alas, that doesn't seem to work in 8.04.. I am but a humble noob but from trawling the forums it seems other people get the same as me: Ubuntu boots to a fuzzy nVidia logo and the drivers have to be uninstalled.. From what I've heard it wasn't a problem in Gutsy.

Then again I only got Ubuntu yesterday so I'm probably utterly wrong!

---

### Post by mathenge on 2008-04-26
I have an NVIDIA 7300. I did a clean install of Hardy yesterday and I had to enable my nVidia driver manually. When I had Gutsy (version 7.10) I used envy to install the driver. However, Hardy seems to have support so I didn't have to.

To get the NVIDIA driver working I used Synaptic. You have to make sure that the restricted repositories are enabled:

 Settings -> Repositories -> Ubuntu Software

Then, the easiest way to find the driver is to search for it. Click on the search button and type "nvidia." The one that I installed is:

 nvidia-glx-new

That seemed to do the trick for me.

---

### Post by DonThompson on 2008-04-27
Thank you, thank you, thank you!!!

I have resolutions and all that's associated with my card!

---

### Post by ShadowWraith on 2008-06-20
I got an error message when I tried to take out nvidia-glx in favor of nvidia-glx-new 
<code>
Removing nvidia-glx ...
dpkg-divert: error checking `/usr/X11R6/lib/modules/extensions/libglx.a': No such file or directory
dpkg: error processing nvidia-glx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx
E: Sub-process /usr/bin/dpkg returned an error code (1)
</code>

---

### Post by captain.kipper on 2008-11-20
> **ShadowWraith said:**
> I got an error message when I tried to take out nvidia-glx in favor of nvidia-glx-new 
<code>
Removing nvidia-glx ...
dpkg-divert: error checking `/usr/X11R6/lib/modules/extensions/libglx.a': No such file or directory
dpkg: error processing nvidia-glx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx
E: Sub-process /usr/bin/dpkg returned an error code (1)
</code>



I had the same error for nvidia-glx-legacy (See my previous post)
[http://ubuntuforums.org/showthread.php?t=963853&page=57](http://ubuntuforums.org/showthread.php?t=963853&page=57)).

$sudo gedit /var/lib/dpkg/info/nvidia-glx*.postrm

and comment out the section regarding libglx.a

rerun apt-get

---

