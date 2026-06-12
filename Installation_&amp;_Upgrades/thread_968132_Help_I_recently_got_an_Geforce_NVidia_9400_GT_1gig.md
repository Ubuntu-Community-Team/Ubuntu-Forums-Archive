---
title: "Help I recently got an Geforce NVidia 9400 GT 1gig"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by buffalosolja on 2008-11-02
I cannot find the driver or maybe I don't know how to install it.  It is so choppy I am having to use my windows partition :(
please help if you can.

---

### Post by khalid7621 on 2009-02-27
I'm having the same problem.  When installing 180.29 drivers, xorg.conf doesn't like what it sees and goes into low res mode.  177 works fine, but no compiz affects.  pls help.

---

### Post by hardwarejunkie9 on 2009-03-01
Make me the third on this list. The maker for the card in my case is Sparkle. It's a Nvidia GeForce 9400 GT and I can't seem to update the drivers.

---

### Post by gadget1186 on 2009-03-02
I also have this video card.  Driver 177 works, but I  cannot get 4x3 aspect ratio resolutions above 1024x768. I cannot get the 180 driver to install at all as I get xserver errors.

Add me to the list of those who need help with this card! I am relatively new to linux so this is a real battle! Editing xorg.conf really looks complicated!

Thanks!

---

### Post by Indubitableness on 2009-03-22
Installing video drivers manually is damn near impossible on ubuntu, and so far no one has been able to figure out why. I've seen it asked and I've asked the question in other threads, and nothin' doin' man. Nothin' friggen doin'.

I just got a GeForce 9400 gt 512 mb here, and I've got the same problem, except that the nvidia-glx drivers don't do anything. I've got the manual install to display properly, but that only lasts until reboot. Then each time you reboot you gotta reinstall manually.

What I don't understand is why ubuntu can't just find the 173 package when I look in system->admin-> hardware drivers.(still on hardy, and 173 is as high as hardy goes for some retarded reason, although you can install the intrepid 177 package on hardy.) 

Of course, we all WANT the goddamned 180 package by now, and it should NOT be this difficult to install. I wish someone could friggen tell us how to fix this 'cause it can't possibly be as difficult as it seems.

---

### Post by norwoods on 2009-03-23
i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.41 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using synaptic package manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
for a fresh install, you might also want or need:
jockey-common
jockey-gtk or jockey-kde
nvidia-settings
nvidia-xconfig

then open System--Administration--Hardware Drivers.
if there is an active video driver, click on it and then click Deactivate
click on the NVIDIA 180 driver
click Activate.
clock Close.

reboot

---

