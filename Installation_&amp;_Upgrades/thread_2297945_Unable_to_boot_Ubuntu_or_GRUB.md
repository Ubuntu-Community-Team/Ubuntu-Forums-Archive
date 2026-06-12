---
title: "Unable to boot Ubuntu or GRUB"
date: 2015-10-07
forum: Installation &amp; Upgrades
---

### Post by GwibberFooey on 2015-10-07
[IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG]
Regarding a new installation of Ubuntu 14.04 - 64 bit on a computer with AMD A6  Vision.:
 At the end of the installation process a window comes up saying  the system must restart to complete the installation. When I restart the  system everything appears to be going smoothly for the first couple of  seconds because a solid purple splash screen appears. But then the  screen goes black and nothing, neither graphical nor text, ever  reappears. However, a few seconds after the screen goes black there is  the sound effect from the normal Ubuntu login prompt (sounds like a  strike on a bongo drum). So it seems like Ubuntu continues loading but  without any video. Maybe X is not loading ? Nomodeset ???
The really strange thing here is that a day or two earlier I used the  exact same iso on the exact same USB stick to load Ubuntu on the exact  same computer, and the entire installation went flawlessly. I decided it  was necessary to reinstall not because of any glitches or flaws or  whatever, but simply to achieve a different configuration.

---

### Post by oldfred on 2015-10-08
Back screen is often video issues, but I do not know AMD.
But I thought nomodeset was required for both nVidia and AMD.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

    
Is system UEFI or BIOS? And did you then install in UEFI or BIOS boot mode?

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Some UEFI systems have fast boot which is a different setting than Windows fast startup. Best to turn that off in UEFI. Or if you can change timing (my Asus motherboard also has that) to have it delay, you then have time to press keys to get into UEFI or one time boot key to get to flash drive or make boot choices.

---

### Post by GwibberFooey on 2015-10-08
I followed oldfred's instruction, "At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.", and I was able to boot into Ubuntu with my existing username and password.  So there is definitely progress. I am still unable to boot into the system without first going into GRUB2 and switching to nomodeset everytime.
Regarding "Post the link to the Create BootInfo summary report", here is the link: [http://paste.ubuntu.com/12716478/](http://paste.ubuntu.com/12716478/) 
And please note, this machine has BIOS; UEFI is not present.

---

### Post by yancek on 2015-10-08
Go to the first link in the post above by oldfred and scroll down on the page until you get to "How to permanently set kernel boot options on an instlled OS", specific instructions are there.

---

### Post by GwibberFooey on 2015-10-08
I have modified the GRUB configuration file according to the instructions in the link. Therefore my system now loads automatically to nomodeset. Ultimately, I would like the system to load the graphical drivers to achieve full video capabilities. How should I proceed in order to accomplish this goal? I think that Ubuntu has the necessary drivers because a few days ago I installed the same version of Ubuntu from the same ISO image onto the same computer, and that installation achieved visibly better graphics without the need for nomodeset.

---

### Post by oldfred on 2015-10-08
I do not know AMD.
With nVidia there are several legacy model drivers for older cards, and installing the incorrect one makes it worse.

 With the upcoming Linux 4.2 kernel will be the première of the new "AMDGPU" 
kernel driver to succeed the "Radeon" DRM kernel driver
[http://tech.slashdot.org/story/15/07/25/2014228/amd-starts-rolling-out-new-linux-driver-model-but-many-issues-remain](http://tech.slashdot.org/story/15/07/25/2014228/amd-starts-rolling-out-new-linux-driver-model-but-many-issues-remain)

   AMD drivers alternatives
[http://ubuntuforums.org/showthread.php?t=2256824](http://ubuntuforums.org/showthread.php?t=2256824)

   open (Gallium3D) and closed-source (Catalyst) driver

---

### Post by GwibberFooey on 2015-10-09
I have installed the AMD Catalyst driver fglrx from the repos using the command ```
sudo apt-get install fglrx
```. Now when I run the command ```
fglrxinfo
```  there is the output:
```
 display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7400M Series
OpenGL version string: 4.4.13374 Compatibility Profile Context 15.20.1013

```
Right now my machine is still booting in nomodeset. How to make the Catalyst driver load up at boot time?

---

### Post by GwibberFooey on 2015-10-10
To make the system boot up without nomodeset and presumably with Catalyst, I did the command ```
gksudo gedit /etc/default/grub
``` and then in the text editor I changed the line ```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
``` to ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```.  Therefore the issue is resolved. Thanks to everybody that helped.

---

