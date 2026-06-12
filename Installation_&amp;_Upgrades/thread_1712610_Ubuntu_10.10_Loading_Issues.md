---
title: "Ubuntu 10.10 Loading Issues"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by Dr. Willey on 2011-03-22
I decided to finally get around to trying out linux but now it I can't get it to work properly. I've looked through these forums and I've found similar issues from the past but I still can't get this to work. I have essentially no knowledge of linux so I'll most likely need to be walked through step by step.

I downloaded the 32-bit desktop version of Ubuntu 10.10 to install onto an old laptop of mine. When I ran the live CD everything worked fine up until the point of trying it out. When I selected that I got the drum beats but the screen remained black with only the cursor remaining. Hoping that the problem resided with the computer trying to run Ubuntu off of the disc I decided to go ahead and install it anyways. Installation went smoothly until it needed to restart where it told me there was an error and the laptop never shut down. I performed a hard shutdown and turned the computer back on and now I am able to get through logging in just fine but afterwards all that appears is the background and the cursor (a step up from the black screen but still just as frustrating). Since I have another laptop I decided to use that laptop solely for Ubuntu and didn't partition the hard drive so I don't think I have GRUB or if I do I don't know how to access it. Other than that nothing seemed to work or I didn't know how to follow other people's advice properly.

Sorry for the essay but I wanted to be as clear as possible so anybody willing to help would have all the information they would need. Thank you in advance for your help!

---

### Post by oldfred on 2011-03-22
Welcome to the forums.

If you have booted thru the log in, then it is not a grub2 boot issue, but another Ubuntu system issue. Often the issue is video related.

If you hold down the shift key from BIOS until menu appears, you should get the grub menu.

You can try recovery mode or this:

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by Dr. Willey on 2011-03-23
Thank you! I now have the taskbar and everything appearing. The background disappeared but I'll assume that was supposed to happen. I'd rather have access to the system over the background anyways. I finally have been able to step foot into the linux community. Thank you again! I'm very grateful for your help. :D

---

