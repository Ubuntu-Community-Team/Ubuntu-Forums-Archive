---
title: "Installation Problems no matter what"
date: 2013-07-10
forum: Installation &amp; Upgrades
---

### Post by Ziykuna on 2013-07-10
Hi

I tried to install a new dual boot and failed hard.
Till yesterday I had win7 and fedora 16

I wanted a  clear win 8 and fedora 19.
Because win8 always tries to create 2 partitions on different hdds I physicly unpluged all my other hdds and installed it.
My plan was too replug everything and install fedora with gub2 - but that didn't work.After several tries I resigned and moved to ubuntu 13.After installing I only got a black a black screen.(Serveral 
times)

I even tried to unplug all other hdds for installation like I did with win8 but that didn't work eather. 

Ubuntu won't boot.I am guessing by now I've got several grubs and mbr on disks.

I am now looking for a clean way to fix my mess.There is no data left to save so I have nothing to worry about.

---

### Post by DeathByDenim on 2013-07-10
So the installation of Ubuntu 13.04 was successful, but after the first reboot you get a black screen? Does it at least show anything before you get the black screen? Like a Grub boot menu or something?

Secondly, since you said you tried to install Windows 8, does your computer have UEFI? I think that's requirement for installing Windows 8, so probably. In that case, you could try disabling "Secure Boot" in the BIOS setup and reinstall Ubuntu 13.04. That might help. I you are unable to disable "Secure boot", then you might want to try disable UEFI altogether. Doing so means you won't be able to install Windows 8 though. (Windows 7 should be fine)

As to the hard drives. You can plug them all in when installing Ubuntu. The computer will just boot from the first hard drive it finds an MBR on. And which one is the first hard drive is determined by the boot order, which you can set in the BIOS setup.

---

### Post by Ziykuna on 2013-07-10
No only a Black screen - no grub no error - nothing ...

I will try to disable secure boot - at least that's something to start with :)

---

### Post by Ziykuna on 2013-07-10
Ok I plugged everything in and the grub from the live usb wrote - secure boot not enabled

I guess that's good.
After installing I still get only a black screen.
No grub no error.

---

### Post by DeathByDenim on 2013-07-10
Is there an option called "Fast boot" in the BIOS? You can try disabling that too.

---

### Post by sudodus on 2013-07-10
If you have Windows 8 installation media (a DVD or USB drive), I suggest that you start from the beginning and install it without UEFI, if your computer can run in old standard BIOS mode, sometimes called CSM in the BIOS menu. Then it will be much easier to install Ubuntu alongside Windows.

But there might also be problems with the graphics driver.

Please describe your computer: brand name and model, cpu, ram (size) and graphics chip/card! It will make it easier to give advice.

---

### Post by Ziykuna on 2013-07-10
It's not a Windows problem because unplugging my Windows hdd and reinstalling Ubuntu didn't change anything.

I've got a 
P8p67 motherboard with a I7 2600k
16gb ram
A Radeon 5950

---

### Post by sudodus on 2013-07-10
Are you running with UEFI? If you have the same black screen also without UEFI, or if UEFI is not involved at all, I think it is the graphics. Radeon graphics might need a proprietory driver. So one way might be to boot in text mode, install that driver, and reboot. But you must reach far enough booting with some live system to be able to install that driver ... If the graphics chip is very new, you have better chances with a very new version of Ubuntu, maybe even the alpha version of 13.10.

---

### Post by oldfred on 2013-07-10
You may need nomodeset, or other boot parameters and/or nomodeset.
 How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Or generic or Radeon setting to get to low quality video to enable installing proprietary drivers:
      
 Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)


[LIST]
[*]Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1
[*]nVidia: nomodeset
[*]Generic: xforcevesa or nouveau.modeset=0
[*]Radeon: radeon.modeset=0
[/LIST]

---

### Post by 1clue on 2013-07-10
Is your goal to have a Windows install and sometimes Ubuntu, or an Ubuntu install and sometimes Windows?

My solution for this would be to install *buntu on the hardware, then Windows on a VM (maybe on kvm or maybe VirtualBox), which would prevent Windows from messing with stuff you think it shouldn't.

This solution would also make it so you can simultaneously run both operating systems, which is infinitely more handy that just running one at a time.

An alternative with similar result would be to install Ubuntu as a VM on Windows.

I'm not telling you not to use dual boot, but frankly I find that worthless in that I have to shut down one OS in order to run the other.  I haven't dual booted in years.

---

