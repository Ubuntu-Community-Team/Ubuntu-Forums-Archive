---
title: "Ubuntu 14.4.2 Install"
date: 2015-06-19
forum: Installation &amp; Upgrades
---

### Post by Carl_Weathers on 2015-06-19
Hi, I'm new to ubuntu and I am having some trouble installing on my laptop. I have an acer aspire 5763z with a Intel Pentium T4500 / 2.3 GHz processor, 8 gigs of ram, and an Intel GMA 4500M graphics card. I bought it off ebay with no operating system, but I can't get ubuntu version 14.4.2 to install; neither the 32 or 64 bit. I am using the live usb install method. I first selected the "Install Ubuntu" option and it froze on the Ubuntu screen with five dots after a half hour or so. I tried again, this time pressing the up arrow at that screen to see the background code running. Most of the processes said "Ok" but anything related to the sound card or Daemon?, has "Fail" at the end. After that I tried the "Try without installing method" and I was able to get to the Ubuntu desktop, but my mouse and keyboard would not function so I had to abandon that. I then tried to install lubuntu thinking the computer was too old to handle ubuntu, but the same installation issues happened. When I tried the "try without install" method for lubuntu I was able to get to the desktop screen, the mouse and keyboard worked, but when I tried to open the Install Lubuntu icon nothing happened.   
I ran the memory test and everything came back clean. I tried the check disk for defects and I received one error so I made a livecd and another usb stick, but the same issues persisted. Any ideas on what the problem could be? 
Also would it be possible for me to remove the hard drive and hook it up as an external drive to my desktop and install Ubuntu from there onto the external? Any help is greatly appreciated.

---

### Post by Bashing-om on 2015-06-19
Carl_Weathers; Hi ! Welcome to the forum .

This may be quite tell-tell :
> 
I tried the check disk for defects and I received one error 

May I suggest you start all over and verify the integrity of the downloaded .iso file ?
see:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by Carl_Weathers on 2015-06-19
I checked the hash values and they are the same. 
Also I removed the hard drive from my laptop, plugged it into an external, connected that to another laptop, removed the hard drive from the second laptop and I was able to install ubunto onto the hard drive. However when I connected it back into the original laptop it said no boot media detected...

---

### Post by oldfred on 2015-06-19
In most cases Intel video just works, but some may need settings. Or you may need some other settings unique to your system.

  Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1

You add the Intel settings like you add nomodeset for nVidia or AMD video.
      
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

My laptop from 2006 has T5500  @ 1.66GHz and 1.5GB of RAM, video is Mobile 945GM. I can install full Ubuntu 64 bit but Unity is so slow as to be unusable. But I prefer and install fallback or gnome panel which is almost the old gnome2 gui but now based on gnome3. With only 1.5GB of RAM I cannot load more than one large app and a couple smaller ones or it starts using swap and is very slow. But for my normal use it is usually ok.

---

