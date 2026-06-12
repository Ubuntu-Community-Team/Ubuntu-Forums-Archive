---
title: "Ubuntu 8.10 Nvidia driver problems???"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Christopher on 2008-10-14
I left Fedora to try the new Ubuntu 8.10 and there seems to be the same problem with video drivers, kernel, MAKEDEV file here, or maybe its something else?. I click on the nvidia driver video card looking thing that popped up and let it install my reccomended 177 drivers and rebooted like it said and i get to a black login screen with the same errors as Fedora gives me. Can someone please help me. Thank you in advance.

---

### Post by tuxxy on 2008-10-14
I belive its the new kernel, search the recent posts as there are already some discussing this problem.

---

### Post by Christopher on 2008-10-14
> **tuxxy said:**
> I belive its the new kernel, search the recent posts as there are already some discussing this problem.

Thank you very much.

---

### Post by JeeZiTsDave on 2008-10-14
I believe that the new kernel has some potential issues with the NV Drivers.  It states it in the Ubuntu Website.  It will definitely be corrected in the nightly builds, but most definitely the Stable Build.

---

### Post by scottslinux on 2008-10-14
I have had the same problem with 8.10 (beta).  I searched the net and found others with this problem.  I think that the NVIDIA drivers are broken in intrepid.  You can log in and run **dpkg-reconfigure xserver-xorg** 
this will reset your x server back.  I found that if I do not upgrade then the playback for DVD's and other video is not smooth and the screen blinks.

I am sure that this issue will be addressed in the coming weeks in the final version.  I guess thats why it is still a beta release. Other than this small issue, I found intrepid ibex to be pretty nice and finally some of the kde 4 issues are being worked out. Keep the faith!

Scott

---

### Post by Victormd on 2008-10-14
I had to use the 173 version with my Geforce 8800GT. On my wife's laptop I installed the 177 version and everything is working fine. Actually, this was the cleanest install (on a laptop) that I've ever seen, everything (even suspend and hibernate) worked out-of-the-box!

Try downgrading the driver to version 173.

---

### Post by eternalnewbee on 2008-10-14
Looking forward to 8.10, but definitely waiting until it's "debugged".
Someone here once said the best thing to do when a system upgrade is available is to wait for like a month, til major issues are solved.

---

### Post by Christopher on 2008-10-14
Im using Ubuntu 8.10 64bit, i have 8gigs of memory would this make any difference?

---

### Post by overdrank on 2008-10-14
Moved to Intrepid Ibex Testing and Discussion :)

---

### Post by wwusnobrdr on 2008-10-15
I too wanted to try out the new Intrepid on my laptop with Geforce 7000M but it looks like its not supported.  The Xorg log file lists all the supported devices, but not the 7000M.  I am trying to use the livecd and the failsafe loads the troubleshooting dialog but I cannot get the desktop.  The bug appears to be here [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/267241](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/267241)

Although mine differs being just one screen so it may actually be another bug.  Never had a problem with any previous ubuntu livecds.  Going to try a liveusb so I can possibly edit the Xorg pre-boot.

---

### Post by mendieta on 2008-10-25
Any update now that we that the 8.10 release candidate is out? I started the upgrade from 8.04, and at some point I got a warning that the binary NVIDIA driver would not work for me, so I canceled and the upgrade exited gracefully. 

The release notes ([http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)) say this:

> 
**[SIZE="4"]nVidia "legacy" video support[/SIZE]**

The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04, are not compatible with the X.Org included in Ubuntu 8.10. Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration.

Users of other nVidia chipsets that are supported by the 173 or 177 driver series will be transitioned to the nvidia-glx-173 or nvidia-glx-177 package instead. However, unlike drivers 96 and 71, drivers 173 and 177 are only compatible with CPUs that support SSE (e.g. Intel Pentium III, AMD Athlon XP or higher). Systems with older CPUs will also be transitioned to the nv driver on upgrade. 


Does this mean that one would need to live with the "nv" driver (no hardware acceleration) forever? Or is NVIDIA expected to release new binary drivers at some point soon? This is all very confusing. 

Thanks!

---

### Post by wgrant on 2008-10-25
You'll have to ask nvidia about that. We don't know.

---

### Post by mendieta on 2008-10-25
> **wgrant said:**
> You'll have to ask nvidia about that. We don't know.

Thanks William, I am aware of the inconvenience of binary drivers, and I try to buy hardware that is natively supported by free(dom) software drivers. I just wondered what the status is, and you just answered my question. Thanks!

Update: I tried the Kubuntu live CD, and I had some issues with the wired internet connection, so I'll wait for final, or maybe the first update to 8.10 - it's not a bad idea to try the live cd first!

---

