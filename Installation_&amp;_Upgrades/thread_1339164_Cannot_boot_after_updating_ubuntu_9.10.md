---
title: "Cannot boot after updating ubuntu 9.10"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by omairaslam on 2009-11-27
Hello

I downloaded the ubuntu 9.10 iso and made a bootable USB from it using lili usb maker. I booted from the USB and everything works fine. It connects to the internet through wifi etc. Now when I update 9.10 and install all the updates and security patches, it asks to restart. When I restart, the menu pops up asking to run in persistent mode. I select it and it remains stuck on 
Running /scripts/casper-premount

and then it displays an error message saying 
"Could not load modules.dep. No such file or directory" and 
"Unable to find a medium containing a live file system". 

I have made the USb 3 times now and in the last attempt I didnt update the grub boot loader but I still faced the same problem. 

I am trying this on an HP tablet PC.

Can anybody tell me how to fix this.

Thanks

---

### Post by efflandt on 2009-11-27
For live/install iso on bootable USB you can add programs and save settings and other data you have room for in your casper-rw (loop mounted persistant file system).  But that does not use grub, and I don't think you should do general system updates, especially not the Linux kernel and modules, because that would not be available when it initially loads the squash / filesystem, before casper-rw is mounted.

If you install a regular system on USB memory/drive, you could then do anything on it that you have room for.  But then near the end of install, you have to pay attention to the Advanced button and put grub2 on the USB device mbr instead of default on your internal hard disk mbr.  I shrunk the vfat partition of a WD Passport with gparted and put Ubuntu 9.10 on ext3 plus swap on that.  But I later had to edit /etc/fstab because it also configure swap that was on my main drive, and that does not exist if booted on another PC.

---

### Post by omairaslam on 2009-11-27
> **efflandt said:**
> For live/install iso on bootable USB you can add programs and save settings and other data you have room for in your casper-rw (loop mounted persistant file system).  But that does not use grub, and I don't think you should do general system updates, especially not the Linux kernel and modules, because that would not be available when it initially loads the squash / filesystem, before casper-rw is mounted.

If you install a regular system on USB memory/drive, you could then do anything on it that you have room for.  But then near the end of install, you have to pay attention to the Advanced button and put grub2 on the USB device mbr instead of default on your internal hard disk mbr.  I shrunk the vfat partition of a WD Passport with gparted and put Ubuntu 9.10 on ext3 plus swap on that.  But I later had to edit /etc/fstab because it also configure swap that was on my main drive, and that does not exist if booted on another PC.
But my issue is that I already know how to make a USB bootable with ubuntu 9.10 running just fine. I am just unable to update it with the latest security patches and updates because then the usb becomes unbootable and it displays the errors mentioned in my original post. 
Can you help me with that ?

---

### Post by darkod on 2009-11-27
Why would you want to update the bootable stick? It's purpose is only to install ubuntu and when it's installed on a hdd you do the updates then.
Similar to windows installation cd, you can't put updates on it. You just download any updates after it's installed.
If I understand you correctly, you are not trying to install ubuntu to usb stick, you are only talking about the bootable startup usb stick with installation files on it. Why the updates?

---

### Post by omairaslam on 2009-11-27
> **darkod said:**
> Why would you want to update the bootable stick? It's purpose is only to install ubuntu and when it's installed on a hdd you do the updates then.
Similar to windows installation cd, you can't put updates on it. You just download any updates after it's installed.
If I understand you correctly, you are not trying to install ubuntu to usb stick, you are only talking about the bootable startup usb stick with installation files on it. Why the updates?
I am updating the persistent installation of Ubuntu 9.10 on the USB. I was of the understanding that I could use it as a permanent thing right off of the USB. All I would need is to carry my USB with the bootable installation on it and just plug it into any PC and have my whole OS with my settings mobile with me. All that is happening fine except when I update the OS with the latest security patches and upgrades after which the USB fails to boot. Correct my understanding if it is wrong. 

Thanks

---

### Post by TheWood on 2009-11-29
Hi

Im looking to do the same thing.

Have a working USB Drive that i can use on any PC to run Ubuntu.

I want to be able to collect mail, surf net etc and have it remember my settings on each boot.

You are correct, this USB can be used to install Ubuntu but id like to use it as a 'live' system that remembers changes made. I do not want to intall Ubuntu to the Hard Disk.

Id like to stay up to date on this USB Drive but as mentioned it this thread when you apply the updates the USB 'live' fails to boot.

I think one poster explained the problem but not with an 'linux n00b' way to resolve this.

Any help will be much appreciated.

TheWood

---

### Post by tkuma on 2009-11-30
I'm beginner linux user, and had same problem with Kubuntu.
We can try install a version only to mount casper-rw and then boot other version 9.10 updated?
If works the second version can be full persistent
Thanks

Sorry, but I speak only portuguese

---

### Post by robl0 on 2009-12-18
Me too. 

Let's pretend I don't own my own computer and want to carry a persistent desktop around in my pocket to run on whatever machine is convenient. It would be nice to be able to update it and not have it get creamed. Can anyone point to, or provide, a step by step on how to do this?

On a slight tangent. I also need to duplicate my setup once I have it setup the way I want, and make a bunch of usb sticks that are the same. Any ideas? 

Thanks in advance :)

---

### Post by darkod on 2009-12-18
> **robl0 said:**
> Me too. 

Let's pretend I don't own my own computer and want to carry a persistent desktop around in my pocket to run on whatever machine is convenient. It would be nice to be able to update it and not have it get creamed. Can anyone point to, or provide, a step by step on how to do this?

On a slight tangent. I also need to duplicate my setup once I have it setup the way I want, and make a bunch of usb sticks that are the same. Any ideas? 

Thanks in advance :)

Have you tried installing on it regularly as a destination? But the stick would have to be 8GB probably, 16GB even better. Ubuntu can be installed on external usb hdd or usb stick, the same as on internal hdd. Just make sure in Advanced option on the last install screen to select the bootloader to be installed on the stick too.
Taking it to another PC might have small driver issues but it should sort them out itself, unless some specific hardware.
That way doing the updates is actually updating the installation. As far as trying to make it persistent USB startup stick as the OP insists, I can't help.

---

### Post by Sid Mact on 2009-12-22
Similar problem here.

 Used 'USB Startup Disk Creator' in 9.04, and 9.10 LiveCD iso.
Told the Creator I did not want persistence, so as to avoid having the casper-rw file in the boot partition (didn't want to do a loop command to see the contents when not booted up in LiveCD mode). Then set up an additional casper-rw partition, so I could add 'persistent' to my boot parms if I desired.

Then copied the fat files from the USB to what used to be my hdd windows (ugh!) boot partition. Also set up a hdd partition named 'casper-rw'. Booted in the hdd Live CD in persistent mode, and ran all the updates, except refused the GRUB 2 installation. Then tried to reboot - and it failed after 9.10 updates, just like everyone else.

THE IMPORTANT PART: I deleted the hdd hard disk files, and replaced with a fresh copy from my LiveCD USB, which was never updated. Rebooted, in persistent mode, and everything works great!

THE LESSON IS THAT THERE IS SOMETHING WRONG WITH THE UPDATES FOR 9.10! THE OLDER VERSION 9.04 WAS ABLE TO UPDATE THE LIVE CD WITHOUT TOUCHING THE FILES THAT WERE CREATED FROM THE READ-ONLY ISO ORIGINAL CD.

I was unable to figure out which individual update trashed which of my Live Cd boot partition files - but that is the only explanation for the update problem!!! Workaround is to keep a copy of the USB boot partition files handy, to restore after the update process. Better would be for Ubuntu to fix the problem.

---

### Post by freescuba on 2009-12-25
I had this same problem and eventually found a solution here that worked for me:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8502730](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8502730)

What I did was to edit my /syslinux/test.cfgto change all references from initrd.lz to initrd.gz  ("l" to "g")

I'm far from a Linux expert so realize while this solution worked for me I don't really understand what cause the problem (or why this even fixes it or if I've introduced other issues LOL) so someone in the know should research this further.

It's a pretty nasty event for anyone using a persistent USB key so I hope the Ubuntu Gods fix this problem.

---

