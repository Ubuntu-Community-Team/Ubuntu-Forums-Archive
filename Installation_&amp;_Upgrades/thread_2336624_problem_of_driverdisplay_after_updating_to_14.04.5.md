---
title: "problem of driver/display after updating to 14.04.5 enablement stack and kernel 4.4.0"
date: 2016-09-09
forum: Installation &amp; Upgrades
---

### Post by rvboutin on 2016-09-09
Hi,
I have an HP PC with an AMD HD8490 video card. The install was a Ubuntu 14.04.2 and it worked fine with the AMD drivers. I need to have the AMD driver running because (maybe bizarrely) the default driver does not work well with a piece of software requiring OpenGL to analyse biomedical images.
Amongst the update requested today, there was one which installed the LTSEnablementStack with the kernel 4.4.0-36. After reboot, I got stuck in the (in)famous login loop, I tried different things before reinstalling this:
[LIST]
[*]linux-generic-lts-xenial xserver-xorg-core-lts-xenial xserver-xorg-lts-xenial xserver-xorg-video-all-lts-xenial xserver-xorg-input-all-lts-xenial libwayland-egl1-mesa-lts-xenial 
[/LIST]
I got back to the desktop and login works fine, however when I tried to load images on my software, it crashed with an OpenGL error message, back to square one, I need the proprietary drivers for the software to work!! Problem I have tried various flavour of the drivers I could find on the AMD website, and none install properly or even at all.
Looking at the supported card, the HD8940 should be supported even in Ubuntu 16.04, but the drivers I can download for that card do not support above 14.04.2.
If anyone has an idea to sort out the situation... that would be very very helpful!!!!
Thanks,
Rv

---

### Post by kurt18947 on 2016-09-09
I don't know details at all but there seems to be an issue with the proprietary AMD driver and 16.04 due to AMD's drivers not supporting the version of xorg found in 16.04 or some such. The solution has been to stay with 14.04 if you need AMD's proprietary drivers. I wonder if your enablement stack including kernel 4.4.0 and maybe the same xorg version used in 16.04 has the same issue. If the problem is something to do with xorg I don't know that reverting back to an earlier kernel would be helpful. Hopefully someone better versed on this with be along.

---

### Post by rvboutin on 2016-09-10
Hi kurt18947,
Thanks for your reply. That's what I feared. Hopefully someone else may have a solution... And hopefully AMD will release drivers for this card in the future for Ubuntu 16.04, as I am not planning to change video card on that PC which is just over 1 year old!!
Canonical have to stop this crazy yearly release and LTS release every 2 years. I work on Linux because it handle file over 2Gb better than Windows and because some scientific software I use run only on Linux; if I chose LTS release it is because I want stability; so drivers being already a pain to install and manage in Linux,when I have a stable system I do not want it being broken by an update!! The enablement stack install should be an active voluntary process not part of an offered update. Keeping system updated for security reasons make sense, but changing versions every year or 2 years or moving to enablement stacks that break systems just for the sake of minor so-called improvement features is a real pain for a work environment. I chose Ubuntu because some software I use are tested in Ubuntu and because Ubuntu is quite easy to install and run, but I am seriously considering moving to another distro!!... rant over...
Anyway, if someone else has another idea, other than restoring the disk image I did 1 year ago... please do contribute!! Much appreciated!
Cheers,
Rv

---

### Post by donbastiano on 2016-09-10
I think you don't have other solution than restoring, but if the original install was a 14.04.2 maybe it is better to install from 14.04.1 (see [https://wiki.ubuntu.com/Kernel/LTSEnablementStack:](https://wiki.ubuntu.com/Kernel/LTSEnablementStack:) "However, if one wants to remain on the original GA stacks, the options are: Install from a previous 12.04.0/12.04.1/14.04.0/14.04.1 point release and update. Previous releases are archived at [http://old-releases.ubuntu.com/)]("http://old-releases.ubuntu.com/")
If I'm not wrong I think your graphic card is not supported by the new AMD closed driver ([http://support.amd.com/en-us/kb-articles/Pages/AMD-Radeon-GPU-PRO-Linux-Beta-Driver%E2%80%93Release-Notes.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMD-Radeon-GPU-PRO-Linux-Beta-Driver%E2%80%93Release-Notes.aspx)) and maybe it will not be supported neither in the future, they are working on previous models but only from GCN 1.0 ([https://en.wikipedia.org/wiki/Radeon_HD_8000_series](https://en.wikipedia.org/wiki/Radeon_HD_8000_series), your card is the "first" not supported ;( ).
So if you want stay with 16.04 you don't have other choice, you have to use the open driver, the old closed driver, fglrx, is not supported in 16.04, is not active anymore and does't work with new X
But wait for someone more skilled :)

---

### Post by kurt18947 on 2016-09-10
From what I've read about AMD & Linix is that they're devoting more effort to improving the open drivers rather than updating the proprietary drivers. There are or will be 2 open drivers, Radeon for older cards and AMDGPU for newer cards. That doesn't help rvboutin today though.

---

### Post by donbastiano on 2016-09-10
Yeah, sorry for "spamming", I was just trying to talk about the driver for that card.
Someone knows if what suggested for example here [https://ubuntuforums.org/showthread.php?t=2266268&page=3&p=13236412#post13236412](https://ubuntuforums.org/showthread.php?t=2266268&page=3&p=13236412#post13236412) is still valid?

---

### Post by rvboutin on 2016-09-11
Hi guys,
Thanks for your posts. I think I'll just restore my system then.
I am however a bit worried for the future if I cannot use AMD card and get OpenGL working!! I am puzzled by the fact that currently OpenGL does not seem to work in the open driver for AMD cards!! What's the point of having a driver for a video card that does not support OpenGL, or at least not as well as the proprietary driver. I hope that in the future the open drivers will fully support OpenGL!!
Cheers,
Rv

---

### Post by kurt18947 on 2016-09-13
> **rvboutin said:**
> Hi guys,
Thanks for your posts. I think I'll just restore my system then.
I am however a bit worried for the future if I cannot use AMD card and get OpenGL working!! I am puzzled by the fact that currently OpenGL does not seem to work in the open driver for AMD cards!! What's the point of having a driver for a video card that does not support OpenGL, or at least not as well as the proprietary driver. **I hope that in the future the open drivers will fully support OpenGL!!**
Cheers,
Rv

From what little I've read, better openGL support in the open source drivers is the path AMD is planning. They (AMD) are on the cusp of releasing a new series of processors so I suspect their attention is not strongly focused on linux support for their GPUs right now.

---

### Post by rvboutin on 2016-09-20
Hi guys,
Thanks for your replies. Regarding the better open-source drivers for AMD cards, I'll believe that once I see it in action :)
I have now restore my PC and all is well again, except that at each reboot the updater asks me to install the enablement stack again! And considering that it breaks my system, I certainly do not want to do that again!! Is there a way to tell the system to turn off the request to install the enablement stack?
Thanks,
Rv

---

### Post by kurt18947 on 2016-09-20
> **rvboutin said:**
> Hi guys,
Thanks for your replies. Regarding the better open-source drivers for AMD cards, I'll believe that once I see it in action :)
I have now restore my PC and all is well again, except that at each reboot the updater asks me to install the enablement stack again! And considering that it breaks my system, I certainly do not want to do that again!! Is there a way to tell the system to turn off the request to install the enablement stack?
Thanks,
Rv

I'm not familiar with the enablement stack so I'm not certain this will help. Synaptic has a means to lock a kernel or package to a certain version for reasons such as yours. If "enablement stack" is listed as a package in Synaptic, perhaps highlighting it then click 'package' 'Lock Version' will prevent more recent versions of enablement stack installing. If there are multiple components making up the 'enablement stack' it may get a little sticky; locking some components but not others could cause a mess.

---

### Post by edwardsah3 on 2016-09-21
I'm running an AMD FX(tm)-4100 Quad-Core Processor × 4  with 15.6 GB of memory, and a Radeon R7 260X/360 card. I found your advice to reinstall 14.04 instead of 16.04 to use the proprietary AMD driver. I did that, but now I have xserver from xenial, apparently backported from 16.04. When I try to install fglrx from synaptic, I get a huge list of files to remove, but I get a warning saying NOT AUTHENTICATED. The list is empty. Considering that I have spent roughly half a day rebuilding a system, I don't want to hose this installation. 
I would also like to know why Ubuntu would put xenial xserver into the only recent LTS that, ostensibly, can run the proprietary driver.

I should point out that when I try to do the same thing with apt-get, I get the following:

root@theory:~# apt-get install fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

---

