---
title: "Install Problem: X Server Failure"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by Smokeymcpawt on 2006-12-01
Hello,

I'm a long time Windows user now attempting to install Ubuntu on my pc so i can enjoy the Linux experience. When loading up the install disk i get an X Server Failure error. 

[IMG]http://arena-zone.com/error/error1.jpg[/IMG]

Here are some more details about the error:

[IMG]http://arena-zone.com/error/error2.jpg[/IMG]

[IMG]http://arena-zone.com/error/error3.jpg[/IMG]

[IMG]http://arena-zone.com/error/error4.jpg[/IMG]


The problem i THINK I'm having is that my dell dimension 3000 has two video cards. I have my Intel(R) 82865G Graphics Controller and my NVIDIA GeForce FX 5200. Or i suspect that it could be my BIOS settings.

I'm thinking that if i disable my NVIDIA card, i can install Ubuntu with my Intel card, and then install my NVIDIA card after Ubuntu is up and running. However, I'll admit I'm pretty much a Linux newbie.

Can anyone confirm my thoughts or suggest any other options? Help is much appreciated.

---

### Post by tommcd on 2006-12-02
Try disabling the on board video in the BIOS, assuming your monitor is using the nvidia 5200. You should have no trouble booting the live CD or installing ubuntu with that video card. If that fails then boot the CD with safe graphics mode.
Also, welcome to the ubuntu forums. Best computer forum of any kind anywhere!

---

### Post by Smokeymcpawt on 2006-12-02
Sorry, i forgot to mention that safe graphics mode doesn't work either.

In my BIOS i have it set to "Auto" For video controller.

---

### Post by tommcd on 2006-12-02
Are you using the nvidia 5200 for windows? Ubuntu should install no problem with that card. I first installed ubuntu breezy 5.04 on that very same card. Does the BIOS give you option to set video to AGP ? If so, set it to that and see if it makes a difference. Perhaps the 2 video chipsets are confusing the installer. I never installed ubuntu on a board with onboard graphics that also had a seperate video card, but I do know the nvidia 5200 should work.

---

### Post by Smokeymcpawt on 2006-12-02
I see no agp option, but i don't think it would help much, my card is PCI.

---

### Post by tommcd on 2006-12-02
Then can you disable the onboard video? If that still does not help then install using the onboard video instead of the nvidia card. Remove the nvidia card if necessary. Then, to add the nvidia card after the install see this thread:
[http://ubuntuforums.org/showthread.php?t=308575&highlight=onboard+video](http://ubuntuforums.org/showthread.php?t=308575&highlight=onboard+video)
and this guide:
[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)
Removing the video card should at least get ubuntu installed for you. Then follow that guide to get the nvidia card installed.

---

### Post by Smokeymcpawt on 2006-12-02
Alright, Thanks alot tommcd.

---

### Post by tommcd on 2006-12-03
Well, I'm interested if you were successful. How did it go?

---

### Post by dross on 2006-12-13
Hi,
I'm having an identical problem trying to install Edgy...but I only have one graphics card, so not sure how to proceed. My card is a
Intel 945GM Graphics.  Anyone have suggestions?  Thanks!

---

### Post by santonucci on 2006-12-13
Having an identical problem myself. 

Machine:
Dell XPS-400 
ATI Radeon X300
Intel Chipset 945P
Dual-Core CPU
Dell EP1945 Monitor (or whatever it is, 19" flat-screen analog). 

Neither Normal or Graphic Safe Mode work. After Ubuntu progress bar gets to the end, the said message appears, and (either after reviewing the error or not) dumps you into a blank screen with a flashing cursor. System responds to no commands, however you can do a soft-reboot or hard-reboot and either times the Shutdown screen appears (screen reminding you to remove any CDs in the disc drive before it restarts) right before the system reboots. 

This bites, as this was my first experience with Ubuntu coming off a smooth experience with Fedora Core. Hope this gets resolved soon!

---

### Post by carlosal on 2006-12-14
Not sure if it's related or not...

I've been installing ubuntus in VMWare virtual machines without problems but...
I've bought a new machine with PIV 3.Ghz, 512 RAM, Serial ATA Seagate Barracuda, ATI Radeon.

I tried to install 6.10 and system freezes in the GNOME screen without displaying the tools under the logo with the foot. The same occurred when I tried Graphics Safe Mode

I tried 6.06 and then the installation (which went OK in VMWare's) cries out 
"/usr/bin/groups: line 57: /usr/bin/id: cannot execute binary file"

When I try to execute 'groups' manually, it shows Segmentation Fault 4ae13b9
Unable to read page block 65fbbfc.

Tried then RHEL 3.0 and it didn't see the hard disk (I guess lack of serial ATA drivers).

So I'm stuck here...

Anyone??

Cheers.

Carlos.

---

### Post by dross on 2006-12-14
This probably isn't the solution that most are looking for, but I just tried installing dapper instead and that works (almost) fine...I got the same xserver problem, but booting to safe graphics mode works in dapper (it didn't in edgy).  That loads the live version, where there's an icon to "install" waiting for you on the desktop.  :)

---

