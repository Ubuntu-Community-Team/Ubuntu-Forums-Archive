---
title: "Cannot load 16.04 over 18.04 - USB Drive/CD ISO file not recognized"
date: 2019-10-14
forum: Installation &amp; Upgrades
---

### Post by mphucul on 2019-10-14
First, I am not a Linux expert and this is my first experience with Ubuntu.  I loaded version 18.04 to load ROS and start playing with robotics.  The project I am following uses Ubuntu 16.04, so I tried to change my install.  NOTE: I am using an HP windows laptop that I loaded Ubuntu over windows.  

To load 18.04 I created a USB stick from the ubuntu ISO file.  I changed the boot order and the laptop booted from the stick as expected.  I then installed 18.04 over the windows installation.  I then noticed that I needed to be running 16.04 for the project I am shadowing.  I loaded 16.04 onto the USB Stick like I did with 18.04 and booted the laptop.  V 1804 ignored the stick and booted from the hard drive.  I tried multiple times and used (and ruined a few) USB sticks with no success.   I then tried creating a bootable DVD but the results were the same.  I created a new 18.04 stick and booted the laptop and this time it booted from the stick (I could tell because the changes I made to the desktop did bot show up).  

I am a complete beginner with Linux (and retired) so I may be missing a step in this process.  Any help would be appreciated.

thanks...

Mike

---

### Post by ajgreeny on 2019-10-14
I have no real idea what you're trying to do but I would be very surprised if you can not use 18.04 in place of 16.04.

Tell us more about the detail of what you need to do that is not possible using 18.04; if it relates to specific GUI requirements in the instructions there may be easy workarounds to get things running as you need.  If the instructions show you command line suggestions which will not work tell us of any error messages you get from running those commands.
And also for me at least, what exactly is ROS as it does not mean anything to me other than something to do with robotics?

If it really is necessary to downgrade to 16.04 you should be able to do so simply by booting from the 16.04 USB, though you may again need to go into the BIOS and set the USB as first priority device; there is no way to downgrade except by a new installation.  Depending on how you created the USB boot device, it may be bootable on a BIOS machine only, not UEFI machine; do you know which was used by Windows or your 18.04 install?

---

### Post by guiverc on 2019-10-14
> **mphucul said:**
>  V 1804 ignored the stick and booted from the hard drive.  I tried multiple times and used (and ruined a few) USB sticks with no success.   I then tried creating a bootable DVD but the results were the same.

if the ISO after being burnt to your stick failed, the most common causes in my mind are imperfect download, or flawed write to media. Did you verify download ([https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)) or validate media ([https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)) though I often use a second box to verify the media if one has troubles with it (ie. if both have trouble with media; it's very likely the media or burn-to-media that was flawed).

The fact that you then had issues with burnt dvd, makes it look more like a failed ISO download, thus the multiple fails on later steps.

---

### Post by mphucul on 2019-10-15
> **ajgreeny said:**
> I have no real idea what you're trying to do but I would be very surprised if you can not use 18.04 in place of 16.04.

Tell us more about the detail of what you need to do that is not possible using 18.04; if it relates to specific GUI requirements in the instructions there may be easy workarounds to get things running as you need.  If the instructions show you command line suggestions which will not work tell us of any error messages you get from running those commands.
And also for me at least, what exactly is ROS as it does not mean anything to me other than something to do with robotics?

If it really is necessary to downgrade to 16.04 you should be able to do so simply by booting from the 16.04 USB, though you may again need to go into the BIOS and set the USB as first priority device; there is no way to downgrade except by a new installation.  Depending on how you created the USB boot device, it may be bootable on a BIOS machine only, not UEFI machine; do you know which was used by Windows or your 18.04 install?

I want to learn how to program robots so I purchased the TurtleBot3 Waffle Pi.  The PC setup instructions call out Ubuntu 16.04 and ROS Kinetic.  I have a laptop that I installed Ubuntu 18.04 a few months ago and I wanted to make sure my laptop configuration matches the instructions.  I don't know if the TurtleBot will work with 18.04, but I do know that I lack the experience to "tweak" the software to make things work.  I tried multiple downloads of the iso file on multiple USB drives and the laptop would never boot from the USB drive (the USB was first in the boot order).  I even tried creating an install DVD but that didn't work either.  The strange part is if I created a USB stick with the 18.04 iso file the laptop would boot from the USB stick.  That is the only configuration where the laptop boots from the USB stick.  Being unfamiliar with Ubuntu I didn't know if there was a config setting that prevented you from installing an earlier version of the OS.  I would reload windows on the laptop and then install 16.04, but I don't have the recovery disks.

---

### Post by mphucul on 2019-10-15
> **guiverc said:**
> if the ISO after being burnt to your stick failed, the most common causes in my mind are imperfect download, or flawed write to media. Did you verify download ([https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)) or validate media ([https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)) though I often use a second box to verify the media if one has troubles with it (ie. if both have trouble with media; it's very likely the media or burn-to-media that was flawed).

The fact that you then had issues with burnt dvd, makes it look more like a failed ISO download, thus the multiple fails on later steps.

I tried multiple downloads and different applications to create the bootable USB stick.  I tried multiple USB sticks from different manufactures.  I did not verify or validate, and it's only the 16.04 version that will not work.  18.04 works just fine.  I'll verify the 16.04 download tonight.  Thanks.

---

### Post by guiverc on 2019-10-15
Quick note:  On some boxes you see a person-in-circle and keyboard-in-rectangle at the bottom of the screen; you need to press a key at this point quickly for the menu to appear which provides the "Check disc for defects" option (disc refers to whatever media is used for Ubuntu-install-image; be it CD/dvd/thumb-drive etc, not your hdd/ssd or where it's going).  On other boxes the menu cannot be missed; but it's BIOS controlled, ie. machine specific which you see (easy to find menu, or the icons & need to press a key for menu to appear).

---

### Post by mphucul on 2019-10-16
> **mphucul said:**
> I tried multiple downloads and different applications to create the bootable USB stick.  I tried multiple USB sticks from different manufactures.  I did not verify or validate, and it's only the 16.04 version that will not work.  18.04 works just fine.  I'll verify the 16.04 download tonight.  Thanks.

I verified the download and I used Ubuntu's Startup Disk Creator to create a bootable USB disk with Ubuntu 16.04.  I rebooted the laptop and it did not boot from the stick.  Verified that USB is first in the boot order.  Any other suggestions?

---

