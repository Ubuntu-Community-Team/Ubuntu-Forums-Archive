---
title: "Should I delete partiton or install new ubuntu over it ?"
date: 2014-07-17
forum: Installation &amp; Upgrades
---

### Post by hebdave on 2014-07-17
Hi there , 

I currently cannot upgrade for my ubuntu hardware support update. If I cannot upgrade due to these reasons and errors below should I delete my partition or do a fresh install over the top of my current partition. The error my 12.04.3 LTS version gives through software update -

Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

The following packages have unmet dependencies:


libgl1-mesa-glx-lts-trusty: Depends: libglapi-mesa-lts-trusty (= 10.1.3-0ubuntu0.1~precise1) but 10.1.3-0ubuntu0.1~precise1 is to be installed
                            Depends: libx11-6 (>= 2:1.4.99.1) but 2:1.4.99.1-0ubuntu2.2 is to be installed
                            Depends: libxdamage1 (>= 1:1.1) but 1:1.1.3-2build1 is to be installed
xserver-xorg-lts-trusty: Depends: xserver-xorg-core-lts-trusty (>= 2:1.11) but 2:1.15.1-0ubuntu2~precise1 is to be installed

This is a separate subject to my prior post elsewhere about my current hardware enablement stack (HWE) going out of support. I have Ubuntu 12.04.3 LTS. I said above about deleting or installing over my current partition as I think a fresh install might be best. Either that or if you know a way to diagnose the error above that I can post hear via a terminal command that may be really helpful. I am a beginner with Ubuntu and may get in a mess with a complex way of doing something hence just starting from scratch could turn out to be easier. 

Thank you for your help.

---

### Post by grahammechanical on 2014-07-17
You accepted the offer to upgrade the Hardware Enablement Stack, did you not? It is not your fault and others have hit the same problem. I have just this morning seen 3 new threads on this problem. To deal with your actual question,

Think. Is the Grub boot menu controlling the booting of the operating systems in the machine? Deleting the Ubuntu partition will not remove Grub from the MBR or UEFI but it will remove the Grub configuration files with the result that Grub will be broken.

So, re-install over the existing installation by choosing the Something Else option. This new install will install Grub into the MBR/UEFI after detecting any other OS. and that will over-write the existing Grub. I have several installations of Ubuntu and its flavours on my two hard disks. I often install over existing installations. I did it twice yesterday when I installed the Utopic Unicorn (14.10 under development) versions of Ubuntu Gnome and Ubuntu Studio. It works fine.

As for the original problem, this is the best that I can come up with

[http://ubuntuforums.org/showthread.php?t=2234830&p=13075611#post13075611](http://ubuntuforums.org/showthread.php?t=2234830&p=13075611#post13075611)

There should not be a problem when we run Network. Unless the router is not switched on or we do not wait long enough.

Regards.

---

### Post by hebdave on 2014-07-17
High I googled the issue about the HWE stack in terms of the specific thing it was - [h=1][Hardware Enablement Stack (HWE) out of support]("http://askubuntu.com/questions/493541/hardware-enablement-stack-hwe-out-of-support")[/h]and it gave me this for the computer I am running [http://askubuntu.com/questions/493541/hardware-enablement-stack-hwe-out-of-support](http://askubuntu.com/questions/493541/hardware-enablement-stack-hwe-out-of-support) . I used the AMD 64 terminal command at the bottom of that askubuntu thread. It seemed say you can get a bug in updating. So I used this and it just updated the HWE - 

sudo apt-get install -V libglapi-mesa-lts-trusty libgl1-mesa-glx-lts-trusty xserver-xorg-lts-trusty xserver-xorg-input-all-lts-trusty xserver-xorg-video-all-lts-trusty libgl1-mesa-dri-lts-trusty x11-xserver-utils-lts-trusty libglapi-mesa-lts-trusty:i386 libgl1-mesa-dri-lts-trusty:i386 libgl1-mesa-glx-lts-trusty:i386 libgles2-mesa-lts-trusty libglapi-mesa-lts-trusty mesa-vdpau-drivers-lts-trusty
To be honest I dont know how much help I am being putting this hear. The command added and removed depencies accordingly so it seemed. this then allowed the update to be installed as well all in the same command. 

I do hope I have not caused a problem further down the line for myself by using the command. Perhaps if someone can look at the above command and tell me if it was not just an inadequate fix I'd know it was legitimately good.

Thanks.

---

