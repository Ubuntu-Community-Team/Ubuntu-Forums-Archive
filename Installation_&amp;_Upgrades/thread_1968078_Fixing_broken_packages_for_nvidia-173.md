---
title: "Fixing broken packages for nvidia-173"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by geovino on 2012-04-28
I'm running 12.04 64bit. and the nvidia drivers that Ubuntu wants to install in additional drivers does not work with my nvidia geforce 6100 video. I used to use nvidia-173 in previous versions of Ubuntu. When I go to Synaptic to install nvidia-173 it says to fix broken packages first. What broken packages? How do I fix it?

---

### Post by haresear on 2012-04-28
I think the nvidia-173 drivers are not compatible with 12.04. I have an nVidia FX5200 card, which used nvidia-173 drivers on all previous Ubuntu versions. When I upgraded to 12.04, it removed the nvidia-173 drivers and installed the nouveau drivers. When I run "Additional Drivers", it now offers no nvidia drivers at all. Can your card use a higher version nvidia driver?

---

### Post by geovino on 2012-04-28
> **haresear said:**
> I think the nvidia-173 drivers are not compatible with 12.04. I have an nVidia FX5200 card, which used nvidia-173 drivers on all previous Ubuntu versions. When I upgraded to 12.04, it removed the nvidia-173 drivers and installed the nouveau drivers. When I run "Additional Drivers", it now offers no nvidia drivers at all. Can your card use a higher version nvidia driver?

I just ordered a EVGA 512-P3-1300-LR GeForce 8400 GS Video Card from Tiger Direct. This card should improve the video. I'm tired of dealing with this onboard geforce 6100 video, its been a problem with other distros in the past. 

I'll see how it goes in a week when I get the new card. :)

---

### Post by zecoyote007 on 2012-04-30
Hi guys,

I found a workaround: keep the 11.10 version of the Xorg server
No conflict at all with any package from 12.04 !!!
nvidia-173 drivers are not compatible with Xorg (ABI to be precise) version released in 12.04.
So I stick with 11.10 version of Xorg. I had to make the following changes to backport Xorg:

1) In /etc/apt/sources.list :

deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) oneiric main
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) oneiric main

2) In /etc/apt/preferences:

Package: xorg xserver-xorg*
Pin: release a=oneiric
Pin-Priority: 1050

3) Note related to nvidia-173/96 on Ubuntu 12.04 (optional if you face slow graphics)
I'm using old hardware with nvidia-173 drivers and I don't like the fact "composite" is mandatory to use Unity correctly (very laggy) I had to force composite to switch it "off" to avoid laggy windows by modifying /etc/X11/xorg.conf:

Section "Extensions"
Option "Composite" "Disable"
EndSection

Bug related to nvidia-173 or nvidia-96, please have a look to this post:
[https://bugs.launchpad.net/ubuntu/+s...73/+bug/922268](https://bugs.launchpad.net/ubuntu/+s...73/+bug/922268)
Enjoy.

Nicolas

---

### Post by mhgsys on 2012-04-30
^ rolling back is not the way to go imo....

I was using the nvidia96 drivers before, but now I'm using nouveau instaid...working like a charm...

---

### Post by sshatery on 2012-05-02
i have the same problem. its keep saying broken package. when i tried to fix it, nothing happened and its still broken. if its not compatible with 12.04 then why its still there?

---

### Post by geovino on 2012-05-07
Installed a nvidia geforce 8400 video card. was able to install additional drivers. Solved my problem. :)

---

### Post by El Zoido on 2012-05-07
I'm in a similar position, my pc at work has a rather old Nvidia card (7300) and I used the 173 driver, as others didn't work at all.
Since Precise I can use the newest one, but get strange graphical corruption in Libreoffice (menus, buttons, etc are all corrupted, restarting fixes it, but only for a while. Seems to be linked to having Firefox running in the background and probably playing videos there).

I suspect it is linked to the driver, but alas, 173 doesn't work anymore.
What I don't get is, why did they even include 173 if it's not compatible with the newest X?

Did also try noveau, but this is making everything extremely sluggish.

---

### Post by rmhurt on 2012-05-28
> **zecoyote007 said:**
> Hi guys,

I found a workaround: keep the 11.10 version of the Xorg server
No conflict at all with any package from 12.04 !!!
nvidia-173 drivers are not compatible with Xorg (ABI to be precise) version released in 12.04.
So I stick with 11.10 version of Xorg. I had to make the following changes to backport Xorg:

1) In /etc/apt/sources.list :

deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) oneiric main
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) oneiric main

2) In /etc/apt/preferences:

Package: xorg xserver-xorg*
Pin: release a=oneiric
Pin-Priority: 1050

3) Note related to nvidia-173/96 on Ubuntu 12.04 (optional if you face slow graphics)
I'm using old hardware with nvidia-173 drivers and I don't like the fact "composite" is mandatory to use Unity correctly (very laggy) I had to force composite to switch it "off" to avoid laggy windows by modifying /etc/X11/xorg.conf:

Section "Extensions"
Option "Composite" "Disable"
EndSection

Bug related to nvidia-173 or nvidia-96, please have a look to this post:
[https://bugs.launchpad.net/ubuntu/+s...73/+bug/922268](https://bugs.launchpad.net/ubuntu/+s...73/+bug/922268)
Enjoy.

Nicolas

Nicolas, thanks so much for posting your solution!  it worked like a charm for me and i would have *never* come up with this solution on my own.  i have an nvidia 5200 in an old motherboard, so upgrading to a newer card isn't really an option.  i wonder tho, how long this xorg pin will continue to work.  maybe i'm stuck at 12.04...?

one thing for novices like myself.  after following your clear steps i wasn't sure what the final step was to cause the xorg downgrade.  i eventually opened up the Synaptic Package Manager and selected "nvidia-173" and that did the trick. 

thanks again - posts like this really help the linux community! :-D

Bob

---

### Post by haresear on 2012-05-28
> **rmhurt said:**
> 

one thing for novices like myself.  after following your clear steps i wasn't sure what the final step was to cause the xorg downgrade.  i eventually opened up the Synaptic Package Manager and selected "nvidia-173" and that did the trick. 

Bob
The final step to downgrade xorg (which was in a follow-up post) is:

sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by r233967 on 2013-03-20
The following simple steps worked for me for version 12.04.02 on March 19, 2013.


- Install 12.04.02 (DO NOT enable auto login).
- When the install finishes rebooting, you will be at the login screen (DO NOT LOGIN).
- CTRL-ALT-F1 to get to a command-line.
- login at the command prompt
- sudo apt-get install nvidia-173-updates (DO NOT INSTALL nvidia-173)
- reboot
- enjoy

---

