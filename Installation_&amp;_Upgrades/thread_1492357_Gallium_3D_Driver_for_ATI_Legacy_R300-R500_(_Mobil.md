---
title: "Gallium 3D Driver for ATI Legacy R300-R500 ( Mobility Radeon x1400 )"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by gillza on 2010-05-24
Hi,

I have recently installed 10.04 on my Fujitsu E8210 laptop and now have a problem with the flickering and noisy screen. I have narrowed down the issue to my ATI mobility Radeon x1400 drivers and seen a suggestion to install Gallium3D drivers. Up 'till now I have installed new kernel from 

[http://kernel.ubuntu.com/~kernel-ppa....34-rc7-lucid/](http://kernel.ubuntu.com/~kernel-ppa....34-rc7-lucid/)

and now am looking for directions on how to install Gallium3D drivers for my video card. I would greatly appreciate if someone could provide step by step directions on how to do it. 

Thank you!

---

### Post by didli on 2010-05-25
Hi gillza !
Look at this thread :
[http://ubuntuforums.org/showthread.php?t=1451727](http://ubuntuforums.org/showthread.php?t=1451727)
There's a PPA for Gallium3D, I think this is what you're looking for.
I'm using it right now (R420 chip) and i'm quite happy with it. 2D performance is astonishing, while 3D is supported but can't nearly compete with ati proprietary drivers (for now).

---

### Post by gillza on 2010-05-25
Thank you!

I have installed the drivers following the update in Sharky's original post ([https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa))

I have also updated my xorg ([https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)) and dropped in the fresh card driver from ([https://launchpad.net/~xorg-edgers/+archive/drivers-only](https://launchpad.net/~xorg-edgers/+archive/drivers-only)). 

All this seems to have helped the matter but did not solve the problem completely. 

Screen sometimes flickers (goes slightly brighter for a split second). While watching Flash videos I have noticed a horizontal line flickering though the screen occasionally. 

Also, the weirdest thing that I have noticed was this: some of the flash videos start to fast forward if I move the coursor while watching them and then result in my WiFi connection being dropped. This is by far the bizzarest glitch I've seen. 

Anybody had similar issues?

Thank you.

P.S. I have reinstalled 10.04 yesterday and will try to update the system, kernel, xorg and Gallium later today...

---

### Post by gillza on 2010-05-25
Bump!

And small update: the issue happens rather randomly. Sometimes it clears up by itself.

---

### Post by tgalati4 on 2010-05-25
Flash is rendered in software and is known to be glitchy.  When watching youtube, you should normally completely cache the file first (hit the pause button and then let it load).  If you try to watch the video in streaming mode, it puts a load on your wireless and your CPU at the same time.  That would explain the dropped connections.

Watch your CPU alongside the video.  Open a terminal:

sudo apt-get install htop
htop

If your CPU goes to 100% while watching a video then you know what the problem is.

---

### Post by gillza on 2010-05-26
Right, except that I had 9.10 installed prior to Lucid Lynx and had no such problems. Even though I had stock ATI OSS drivers 3d acceleration was decent and flash, although cpu hog, was never a problem. This screwed up screen and dropped wireless issue is a "feature" of 10.04 LTS.

---

### Post by gillza on 2010-05-26
I reinstalled 10.04, then 

**sudo gedit /etc/default/gru**b

pasted radeon.modeset=0 into GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

so it will look like this: 

**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.modeset=0"**

saved it and ran **sudo update-grub**

reboot and it looks like the issue has been solved, no need to install anything else.

Note: if the grub is updated later you will have to go in and add radeon.modeset=0 again.

P.S. When I had gallium 3D installed this fix screwed up the video driver completely and thus I decided to reinstall the system instead of trying to remove it

---

### Post by avengerxp on 2010-10-06
my Ati x1950 (R570 chipset) works sluggish in ubuntu 10.04 using the default drivers. and i badly want 3d support as well.

do you suggest the gallium drivers??

how safe are they??

how can i install them.


thanks in advance

---

### Post by gillza on 2010-10-06
> **avengerxp said:**
> my Ati x1950 (R570 chipset) works sluggish in ubuntu 10.04 using the default drivers. and i badly want 3d support as well.

do you suggest the gallium drivers??

how safe are they??

how can i install them.


thanks in advance

My x1400 card works ok with the open-source driver. If you'd read the posts above you will see my explanation of how I installed the gallium3D. I am in no position to suggest Gallium3d since as explained above I have performed the clean install and used the stock drivers with the quick fix to kernel loading parameters trough grub. 

In you private message you said you need 3d support and you cant play videos. The native player that comes in ubuntu is shiet.
Install VLC or mplayer (follow andrew.46 guide [http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)). And use the search button or [www.googlubuntu.com](www.googlubuntu.com). All the info is out there, don't be afraid to experiment and mess up your linux install...

---

### Post by avengerxp on 2010-10-06
ok.

so far i have done 5 fresh installs of ubuntu LTS... every time screwing up the install trying to install VGA drivers..

LOL

i will keep on trying.

PS..
I installed VLC.. it's even worse... renders each frame like slide shows...

---

