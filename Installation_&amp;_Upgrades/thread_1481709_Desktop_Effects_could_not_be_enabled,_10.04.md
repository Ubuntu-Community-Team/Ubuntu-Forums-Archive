---
title: "Desktop Effects could not be enabled, 10.04"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by RHogskin on 2010-05-12
I installed Ubuntu 10.04 using Wubi. After some initial problems, I was able to get desktop effects to work properly. They suddenly quit working and have tried several solutions from the forums, but so far nothing has worked. Now, desktop effects won't work and the hardware drivers utility tells me that "no proprietary drivers are installed on my system" which is not the case.

---

### Post by PrivateLifeOfPlants on 2010-05-14
I am having the same issue after upgrading, I can not enable desktop effects. Any ideas?

---

### Post by PrivateLifeOfPlants on 2010-05-14
Okay, I fixed it now by uninstalling nvidia

sudo apt-get remove nvidia*


and installing the intel driver listed on this page:




[https://help.ubuntu.com/community/RestrictedDrivers](https://help.ubuntu.com/community/RestrictedDrivers)

---

### Post by 300Z on 2010-05-16
> **PrivateLifeOfPlants said:**
> I am having the same issue after upgrading, I can not enable desktop effects. Any ideas?
Same here.
Everything was working fine but after doing an update today and reboot now the desktop effects can not be enabled, every time I try to enable it it does a "search for available drivers" then gives me a message saying that the effects can't be enabled... 
Any clues? :confused:

---

### Post by comadreha on 2010-05-17
> **300Z said:**
> Same here.
Everything was working fine but after doing an update today and reboot now the desktop effects can not be enabled, every time I try to enable it it does a "search for available drivers" then gives me a message saying that the effects can't be enabled... 
Any clues? :confused:


I had the same problem with you! In fact i use the nvidia drivers. Therefore i reinstalled the driver and now works fine !!!

---

### Post by 300Z on 2010-05-17
> **comadreha said:**
> I had the same problem with you! In fact i use the nvidia drivers. Therefore i reinstalled the driver and now works fine !!!

Yeah, I just did the same here (reinstalled the ATI drivers) and it's all fine now.

---

### Post by Grace_11 on 2010-06-05
same problem with me.
before it was working.
now i cant able to change my desktop background to Normal

---

### Post by theGOPman on 2010-07-30
I had the same problem after upgrading to 10.04 and tried a number of things to fix it. Then I found this post which might explain why glxinfo returns a BadRequest.

[https://www.redhat.com/archives/fedora-devel-list/2006-February/msg01178.html](https://www.redhat.com/archives/fedora-devel-list/2006-February/msg01178.html)

I re-installed xserver-xorg and I'm back running compiz with Desktops effects :D

To re-install xerver-xorg, see the below:

[URL="http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-"]http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html
[/URL]

---

### Post by rmcellig on 2010-08-14
In my case I am running Ubuntu in VMware Fusion (Version 3.1.1 (282344) for the Mac. What should I do to get Desktop effects working?

)

---

### Post by lgmanuel on 2010-08-31
> **rmcellig said:**
> In my case I am running Ubuntu in VMware Fusion (Version 3.1.1 (282344) for the Mac. What should I do to get Desktop effects working?

)

same problem guys, need help..

here is my VGA driver..

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

..now how do i remove it, and reinstall...

i installed Lucid Lynx under windows 7 using Wubi..

help.

---

