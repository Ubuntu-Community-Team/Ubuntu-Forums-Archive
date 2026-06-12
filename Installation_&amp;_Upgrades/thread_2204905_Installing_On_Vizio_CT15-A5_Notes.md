---
title: "Installing On Vizio CT15-A5 Notes"
date: 2014-02-10
forum: Installation &amp; Upgrades
---

### Post by erhollowell on 2014-02-10
I am doing this post as a record of my install of Ubuntustudio 13.10 on a new Vizio CT15-A5 laptop.

At this point I have found that the way to the BIOS settings is by repeated pushing of the F2 key. Just pushing and holding the key won't work. Had to go to Vizio support to learn that as they don't publish much technical info. Most support FAQ answers start.."Go to Windows Settings control panel...".

The system is built around an Intel I7-3517U with Intel HD 4000 graphics. At this point I have not attempted to install Ubuntu to the 256G SSD drive. I am planning on replacing the installed drive with a new drive later this week. Then I will install as a Ubuntu only system and save the delivered drive for warranty issues or resale if I decide I don't like the results.

At this point it is running nicely as a live session from a USB drive. As it first booted the audio controls were not right but after about 300 Mb of updating it is now good. I haven't tried the HDMI yet so I can't say whether the HDMI sound is up. Microphone is good. Web cam I haven't tried. Some of this stuff is heavy lifting so I am waiting for the full install before worrying.

The only major issue is that the WiFi seems to drop frequently. I think there may be an issue in those drivers.

I can't seem to set the clock time, and it's not synced to the mobo clock which I did set, but haven't spent time on that.

Touchpad support seems good and I already like the touch pad more than most others I have used.

Haven't tried bluetooth yet.

New mSSD is due Wednesday. Any Ideas on tasks to do before I try full install?

---

### Post by erhollowell on 2014-02-11
Well I found out that the wifi works well as long as I don't leave the router control page up. I am connected to a wireless hot spot and leaving the control page up to see the wireless signal quality. Somehow this is causing data failuers at odd intervals.

---

### Post by erhollowell on 2014-02-13
I have installed the new drive and the drive is recoginized by the BIOS after some reboots. I first attempted to install to the new drive from a live sesson failed. Then I tried to install directly and I got GRUB. I tried many different ways but the furthist I can get is a command line after the GRUB menu reading [Gave upwaiting for root device. Common problems: 
Boot args; 
Check root delay; 
Check root; 
Missing Modules;  
ALERT!  /dev/mapper/ubuntu--studio--vg-root does not exist. Dropping to a shell!   
BusyBox v1.20.2 9ubuntu 1:1.20.0-8.lubuntu1) built-in shell (ash) Enter 'help' for a list of built-in commands.]

(initramfs)  _

This is as far as it appears I can go tonight. Anyone know the magic words? If not i must dig deeper....tomorrow.

---

### Post by erhollowell on 2014-02-15
Big progress today after several more hours of frustration. I tried installing from a DVD instead of the flash drive and got much better results. I can only assume that something in 'install from live' or in installing from the USB flash drive effects the way the hard drive is partitioned in a bad way. I did get some progress when I went in and set the drive map myself. somehow I don't think the mount point was being set properly. Once I burned a DVD and installed from the USB DVD/CD drive it was just a matter of making sure the boot order was set properly.

One other problem I never solved was the whole disk encryption. It seemed that GRUB has trouble in brining up the window to enter the decrypt code. I would just get the changing color dots screen until timeout was reached.

I almost forgot about the encryption problems after I got 13.10 running. God does it run! I get power on to log in screen in about 8 sec. Suspend comes in less than 1 sec. and awake from suspend happens in about 3 sec. Everything seems to be working 100% after the post install update. I installed G UVC Video and the camera and audio all seem to run great too.

I am feeling happy right now so i would tell anyone Ubuntu on a Vizio CT15-A5 works nicely IF you can get it installed sucessfully and I did not worry about Windows8 so if you have to have a duel boot you might have a struggle. I would also say it shoulden't bee this difficult and one of the reasons I've been an Ubuntu user for the past 5 years is that it always seemed to be so easy to install. I worry about the future if these problems don't get resolved soon because most people won't go to the trouble I have.

Also note that the HDMI out seems good including the audio.

---

