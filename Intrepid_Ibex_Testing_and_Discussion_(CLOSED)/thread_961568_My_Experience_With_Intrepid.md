---
title: "My Experience With Intrepid"
date: 2008-10-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Megatog615 on 2008-10-28
Here are my current issues:

CD-Drives: I am having this strange(yet very humorous) issue with my CD/DVD drives. If I open the drive and it contains a CD in it, the drive will automatically close once it opens completely, which is kind of annoying considering I want to remove the disc on the tray. I have no idea how to troubleshoot this as this is a completely new kind of issue for me to handle.

Usplash: At first, when I upgraded to Intrepid, Usplash would hang at "Waiting for the root filesystem" and drop to a console eventually with an error about /sbin/v86d. I have since fixed the error(I think) by installing v86d in a recovery session(as well as installing the nvidia drives in the same session). Now, if I leave splash enabled on the kernel command line, my monitor loses connection and drops to standby mode, and I never get video. I think it might have something to do with the nvidia drivers and v86d.

Buffer I/O Errors on Startup: On bootup, after the v86d hang, I also got buffer I/O Errors for /dev/sr1. Now, if I recall correctly, /dev/sr1 is the real CDROM device file(which /dev/scd1 points to). Why on Earth would something be wanting to write to a read-only CDROM device file on bootup? At this point I have to empty both of my optical drives for the system to boot.

Compiz: Compiz still breaks SDL OpenGL games such as ioQuake3 and Tremulous. It doesn't mess up the window anymore(making it windowed mode automatically and switching fullscreen and windowed like crazy), but it does mess up the mouse control(disabling it completely). Compiz is getting there but I think I will have to opt out of Compiz for this release(as I have with every other release) unless this is fixed or there is a workaround to getting mouse input working.

Here is where it gets better :):

Other than these issues Intrepid is working fine. I like the new DKMS module service. I noticed it installing the NVIDIA driver and was very impressed with the way it worked. My cx18-based Hauppauge HVR1600 is supported by the kernel which means I don't have to install the drivers every kernel update anymore, which is nice. I like the user switching applet and that it is integrated with Pidgin.

I hope the issues I described get fixed before Intrepid is rolled out on the 30th, else we'll have a release like we had with Edgy.

---

### Post by kansasnoob on 2008-10-28
Regarding the CD tray problem we did find a work-around. Read posts #25 and #27 here:

[http://ubuntuforums.org/showthread.php?t=942553&page=3](http://ubuntuforums.org/showthread.php?t=942553&page=3)

---

