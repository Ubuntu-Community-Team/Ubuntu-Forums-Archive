---
title: "Kernel upgrade + proprietary video driver in use=no gui.  Why?"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by Handssolow on 2010-12-11
Some do and some don't, what's the explanation?
Some will be familiar with the events here. I install a new kernel, reboot and am left with a black screen, text login and no gui. Drat, I should have removed the nVidia proprietary video driver before agreeing to the new kernel. After playing around with recovery mode and removing the driver, I eventually get the proprietary video driver working with the new kernel.

I've two almost identical PCs-
1. Has a PCI GeForce 6610XL video card and a old CRT monitor which seems to accept kernel upgrades with little bother.
2. Has a AGP GeForce 6600GT and a Samsung SyncMaster LCD/TV with res 1024X768 where a new kernel means I've about 20 minutes of reboots before I'm back to normal.

Questions.
Before the kernel upgrade would the upgrade have been helped if I had already chosen a low res graphics mode and saved that configuration?

Or, if I forget to remove the graphics driver before I'm dumped to a text login screen, what would be the command line commands to get the proprietary video driver working with the new kernel?

---

### Post by Handssolow on 2010-12-20
Same again, I install 2.6.35-24-generic-pae and no graphical interface appears even though during the install I see a message about the nvidia driver being associated with 2.6.35-24-generic.

I get a gui with the previous kernel 2.6.35-23-generic-pae (recovery mode) and remove the nVidia driver. Back into 2.6.35-24-generic-pae (recovery mode) and from safe mode graphics, re-install the nVidia driver.

Perhaps this will keep happening with new kernels until I ditch my AGP card.

---

### Post by Frogs Hair on 2010-12-20
I had to remove the Nividia driver for kernel updates in 9.10 but I did not have problems with 10.04 or currently with 10.10 . This may be a good question for the Ask Ubuntu site. My computer is less than a year old so I don't think this is an old hardware issue.

---

### Post by PelPix on 2010-12-20
I'm having the same problem with my radeon.  Can anyone walk me through removing FGLRX using only command line?

---

### Post by spcwingo on 2010-12-20
> **Handssolow said:**
> Some do and some don't, what's the explanation?
Some will be familiar with the events here. I install a new kernel, reboot and am left with a black screen, text login and no gui. Drat, I should have removed the nVidia proprietary video driver before agreeing to the new kernel. After playing around with recovery mode and removing the driver, I eventually get the proprietary video driver working with the new kernel.

I've two almost identical PCs-
1. Has a PCI GeForce 6610XL video card and a old CRT monitor which seems to accept kernel upgrades with little bother.
2. Has a AGP GeForce 6600GT and a Samsung SyncMaster LCD/TV with res 1024X768 where a new kernel means I've about 20 minutes of reboots before I'm back to normal.

Questions.
Before the kernel upgrade would the upgrade have been helped if I had already chosen a low res graphics mode and saved that configuration?

Or, if I forget to remove the graphics driver before I'm dumped to a text login screen, what would be the command line commands to get the proprietary video driver working with the new kernel?

It sounds like you didn't install DKMS (dynamic kernel module support).  All that it does is installs the nvidia (in your case) module in the new kernel at install time.  I used to have this same problem too, but now after using DKMS I've never been booted to the cli.

---

### Post by Frogs Hair on 2010-12-20
The DKMS should be installed by default , but check the synaptic package manager to be sure.

---

### Post by efflandt on 2010-12-20
If you install/activate proprietary drivers from the Ubuntu repos, using System > Adminstration > Additional Drivers (or Hardware Drivers 10.4 or earlier), or using Synaptic or apt-get, there should be no problems updating kernels (but I have only done regular 32 and 64-bit kernels, not pae).

If you need newer drivers than the standard drivers for that Ubuntu version, you can often get newer drivers for Maverick (and nvidia for Lucid) by adding x-swat repositories [http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
```For example for nvidia then just use Synaptic to reinstall nvidia-current, nvidia-settings, and nvidia-current-modaliases (not sure which for fglrx) and reboot.

However, if you manually installed video drivers from the manufacturer's website (like nvidia.com), then the Update Manager knows nothing about them, and you may need to reinstall your video drivers after kernel updates, because the video modules will be missing from the new kernel.

---

### Post by Handssolow on 2010-12-21
Thanks spcwingo, I've re-installed DKMS just in case.
Thanks efflandt, I've bookmarked your posting.
I'm currently piecing together parts for a newer PC and my next video card will be smokin'. Well not literally I hope.

---

### Post by Handssolow on 2011-01-27
Today I eventually upgraded with a working gui to 2.6.35-25-generic-pae but it took far longer that I liked.

I needed to remove the proprietary nVidia driver from the previous kernel then reboot to the new in low res graphics before installing the video driver. It took about an hour to get it sorted.

---

