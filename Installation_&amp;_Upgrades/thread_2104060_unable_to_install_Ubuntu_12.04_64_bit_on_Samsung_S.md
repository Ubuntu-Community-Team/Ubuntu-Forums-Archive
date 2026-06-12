---
title: "unable to install Ubuntu 12.04 64 bit on Samsung Series 7"
date: 2013-01-11
forum: Installation &amp; Upgrades
---

### Post by spokeydokey on 2013-01-11
Hi

I'm trying install Ubuntu 12.04 64 bit on a Samsung Series 7 (700Z5C-S01US), dual boot with Windows 7.  The laptop is brand new.  I accidentally installed the 32 bit version (which was working great), then decided to reinstall the 64 bit version.  

While in Windows, I shrank the largest partition to give myself about 600 GB of unallocated space to install Ubuntu.  I also deleted the laptop's 8GB ExpressCache partition (iSSD on the motherboard) so I could create swap space in Ubuntu.  (Again, the 32 bit version worked fine with this setup.)

I downloaded the 64 bit iso file, and used Pendrive to create a bootable USB stick.  I changed the boot order in the BIOS setup to start with the USB.

I shutdown the laptop, inserted the USB stick and booted up.  I got an option to run Ubuntu, install Ubuntu or check for errors.  First I checked for errors, then I selected the option to install Ubuntu.  I got the screen with the five dots, then everything went blank.  I waited (probably a half hour), but the screen remained blank.  So I shut down and tried again.  Now, whether the USB stick is in or not, when I boot up, the computer screen stays blank (no light at all).  It doesn't appear to even get to POST.  

I'm not sure what options I have.  I can't boot to Windows, and I can't get to setup for BIOS.  When I power on, the power light comes on, and the hard drive light comes on for a second then turns off.  The screen remains off.

Any suggestions?

Thanks!
spokeydokey

---

### Post by fantab on 2013-01-12
Welcome!

Looks like a bad burn to me.
First of all check the integrity of you downloaded .iso using [**MD5SUM CHECK**]("https://help.ubuntu.com/community/HowToMD5SUM"), if there any issues re-download (preferably using a [torrent]("http://www.ubuntu.com/download/desktop/alternative-downloads")). Burn it to the USB... It should work.

---

### Post by spokeydokey on 2013-01-12
Thanks for the reply.  The iso file is on my Samsung, which I can't boot, so I can't check its integrity.  

I don't think it's a bad burn though.  I had the identical problem on another Samsung laptop prior to trying it on this one.  I ran the issue by a IT guy at work and he thought the screen light was burnt out and suggested I return the laptop, which I did.  So actually, this is my second attempt at installing 12.04 64 bit and I'm running into the same problem.

---

### Post by spokeydokey on 2013-01-12
I tried creating another USB stick with 12.04 32 bit, but that won't boot either now.  ](*,)

I should have bought a new Thinkpad (which is what I'm typing on now.)

---

### Post by Arthur P on 2013-01-20
Sounds like you ran into this bug: 

**UEFI boot live-usb bricks SAMSUNG 530U3C,np700z5c laptop**

[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)

Samsung should of course have immediately come out with a BIOS update to fix this fatal bug in their BIOS for this computer and the one or two others that have the same bug. Until such time Samsung should post a clear warning on their websites globally that this is being addressed and what methods can be used to safely install Linux until a proper BIOS update is available.

Seemingly the latest daily builds for Ubuntu 12.04 have a kernel which avoids this fatal bug, but that is imho a workaround which still retains risk if eg you were to update to 12.10 automatically with an unpatched kernal being installed, or with other software somehow activating the same problem. The real fix should be Samsung coming with a corrected BIOS asap.

---

