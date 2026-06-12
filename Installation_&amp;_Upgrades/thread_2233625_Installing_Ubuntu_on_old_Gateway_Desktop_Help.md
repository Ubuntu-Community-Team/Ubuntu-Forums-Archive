---
title: "Installing Ubuntu on old Gateway Desktop Help"
date: 2014-07-09
forum: Installation &amp; Upgrades
---

### Post by James_Melhuish on 2014-07-09
I've been trying for the last couple of hours to install ubuntu 14.04 64 bit on a old gateway desktop. I've tried both a usb stick and dvd that have both worked on previous installs on other desktops so there is no problem there. When I boot to the usb or the dvd the window to pick a language comes up, I pick english  and then the window to choose what to do comes up, and I pick install. Then the screen goes black and prints some text to the screen and stops. I left the computer when it stopped for 30 minutes and came back to the same screen. The computer has an amd phenom x-4 quad-core chip and 4 gigs of ram. There is also a graphics card and tv tuner that were already in the computer when it was given to me. Any help would be greatly appreciated.

---

### Post by nknwn on 2014-07-09
"Then the screen goes black and prints some text to the screen and stops"

What does the text say?

---

### Post by ibjsb4 on 2014-07-09
Take a look at this thread

[http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by James_Melhuish on 2014-07-09
Sorry about the vague terms. It goes into a command line right after I hit install. I can't scroll up but it always stops on this text and stays there:
sd 6:0:0:0: attached scsi generic sg2 type 0
sd 6:0:0:1: attached scsi generic sg3 type 0
sd 6:0:0:2: attached scsi generic sg4 type 0
sd 6:0:0:0 [sdb] Attached SCSI removable disk
sd 6:0:0:0 [sdc] Attached SCSI removable disk
sd 6:0:0:0 [sdd] Attached SCSI removable disk
sd 6:0:0:0 [sde] Attached SCSI removable disk
random: nonblocking pool is initiated

It always stops there and I left for 30 minutes to come back to this same bit of text. Hope this helps

---

### Post by nknwn on 2014-07-09
To me the text does not seem to give much info.
Does a Ubuntu live disk run all the hardware?

If it does not then that might point to the reason for the install failure.
Say there was a dodgy hard drive - that can certainly prevent a successful install.

---

### Post by oldfred on 2014-07-09
You mention old system, how old?
Also what processor and video card/chip?

Full Ubuntu or Kubuntu needs a newer system with decent video system. If limited RAM Lubuntu may be a better choice.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by James_Melhuish on 2014-07-10
I removed the video card and ubuntu installed without a problem. I was given the the desktop by a friend and don't know what the video card is. Is there a way to find out? I would like to use the video card if I can.

---

### Post by oldfred on 2014-07-10
If you have the video card out, it should have brand & model on it. 
If you have dual video then are you booting with Intel video on chip. Then it may not be so old?

Only if plugged in (and working?)
 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root
What is installed
dkms status

---

