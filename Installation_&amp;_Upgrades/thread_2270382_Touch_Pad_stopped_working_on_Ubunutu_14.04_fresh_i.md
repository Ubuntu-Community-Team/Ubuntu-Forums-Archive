---
title: "Touch Pad stopped working on Ubunutu 14.04 fresh installation"
date: 2015-03-22
forum: Installation &amp; Upgrades
---

### Post by harold5 on 2015-03-22
Hi All,

I installed Ubuntu 14.04 64 bit on my Fujitsu Lifebook U series laptop and my touchpad stopped working. It working with the previously installed Ubuntu 14.04 32 bit system.

I tired reinstalling the xorg and got the following errors:

sudo apt-get --purge autoremove xserver-xorg-input-all && sudo apt-get install xserver-xorg-input-all

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'xserver-xorg-input-all' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libcheese-gtk23 : Depends: libclutter-gtk-1.0-0 (>= 0.91.8) but it is not going to be installed
                   Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
 libcheese7 : Depends: libclutter-gst-2.0-0 (>= 0.10.0) but it is not going to be installed
              Depends: gstreamer1.0-clutter but it is not going to be installed
 libclutter-1.0-0 : Depends: libcogl-pango15 (>= 1.15.8) but it is not going to be installed
                    Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.



Looks like I missed a package to two on the installation. 

I would like to get the touch pad functioning and am wondering if anyone had a suggestion on how to fix this problem?

Cheers

---

### Post by veddox on 2015-03-23
Hello Harold,

had the same problem some time ago with Gnome under Arch Linux - the problem was a missing Synaptics touchpad driver. Unfortunately I don't know which Ubuntu package contains this, have a look around the repository. (Under Arch it's called xf86-input-synaptics.)

I doubt whether xorg has something to do with it, though it might.

But before you dive into the repo depths, have you tried the control center? Check the settings for the touchpad there, perhaps it's disabled for some reason or another. (Sometimes the touchpad gets disabled when a USB mouse is attached.)

Hope that helps :-)

---

