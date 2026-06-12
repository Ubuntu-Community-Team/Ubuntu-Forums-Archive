---
title: "Ubuntu 12 help installing off USB stick"
date: 2013-04-19
forum: Installation &amp; Upgrades
---

### Post by kkoz83 on 2013-04-19
Hello everybody, how are you?

I have Ubuntu 12.04 (32-bit) installed on a flash drive.  I have a problem with installation.

When I boot in desktop PC - no problem.
When I boot in laptop - stuck issue.

It gets stuck on the Ubuntu logo with all the dots filled.  When I tried to press F6, all looks good except it fails on "stopping cold plug devices".
The desktop is using the motherboard's graphic card & laptop has a SSD drive.

I'm brand new to Ubuntu so please be precise in hour answers.  Thanks :)

---

### Post by oldfred on 2013-04-19
It seems that is one of many normal shutdown lines. It is shutting down after something else errors? Or is that the only error message.

What video does laptop have. How much RAM? If more than 3GB you probably should use 64bit version, but that probably will not fix your current error.

---

### Post by kkoz83 on 2013-04-20
That's the only line that fails.  I'm not sure on the laptop's video specs (guessing ATI) but 4GBs of RAM & it is an Asus K53Z-BBR3 & new SSD.
I tried it on my friend's 2 year old Toshiba laptop and it worked without any issues.

---

### Post by oldfred on 2013-04-20
Some with various Asus have posted these comments:

>  Asus m4a87td  core unlocker feature on usb3 was causing the problem
Asus - Security> I / O interface Security> "New interface card" or so. SET IT TO LOCKED!!! 
In the Asus BIOS I selected Advanced Mode>Advanced>SATA Configuration.
Changed IDE Mode to AHCI Mode
Then,when the SATA3G_1 selection appears in the drive list below,select the Enabled option.
set pci=nomsi or other boot paramter



---

### Post by kkoz83 on 2013-04-20
Thanks for the info.  I'll try it within 48 hours.
Quick ? - the line "Asus - Security> I / O interface Security> "New interface card" or so. SET IT TO LOCKED!!" - is that in BIOS or Windows 7?

---

### Post by oldfred on 2013-04-20
I assume that is BIOS. And I would think it should be unlocked, but that is what the OP posted.

---

### Post by kkoz83 on 2013-04-20
Okay, I'll try ASAP.

---

### Post by kkoz83 on 2013-04-20
I kept the USB I/O to unlocked (if I "lock" then it disables all USB ports).  I did change SATA.  All that but no luck.
So where I had the option to chose "Default, Help, Try..., Install" etc, I pressed "TAB", then typed nosplash noquiet nomoodeset.  Then I pressed "Enter" & got it to appear but in a primitive look - like safe mode for Windows.  I squeezed Ubuntu to 14GBs & all installed correctly.

Now when I turn the laptop, I see which OS to choose (Ubuntu in spot 0 & Windows 7 in spot 4).  After I chose Ubuntu, I heard it "log on" but freezes on all-purple screen.

My question - Do I always need to add "nosplash noquiet nomoodeset" to option while starting Ubuntu?  Do I use all 3?  What does each do?

Thanks so far!

---

### Post by oldfred on 2013-04-20
Nomodeset is a default for video. If having issues I remove splash and quiet as that is what hides the boot process and shows the purple screen & logos. I want to see if boot process stops for any reason. That same info is copied into the demesg log file for later review as it does go by quickly.

Nomodeset is just a basic video usually not good quality. I have nVidia and install the nVidia drivers first thing. AMD has its drivers if a newer card and normally Intel just works, but sometimes needs a default to start. If Optimus you then need Bumblebee.
Each has different ways to update.

What video card/chip do you have? There are many threads on each if you want to search also.

---

### Post by kkoz83 on 2013-04-21
I have AMD Radeon(TM) HD 6480G

---

### Post by oldfred on 2013-04-21
I have nVidia, so do not know AMD.

 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)
sudo apt-get install fglrx
#sudo aticonfig --initial -f
sudo aticonfig --adapter=all --initial
After reboot to get Catalyst Control Center
sudo apt-get install fglrx-amdcccle

   [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
[http://ubuntuforums.org/showthread.php?t=1558406](http://ubuntuforums.org/showthread.php?t=1558406)

---

### Post by kkoz83 on 2013-04-21
Should I try the "sudo..." lines?  How do I get a terminal window if I can't get into Ubuntu?

---

### Post by oldfred on 2013-04-21
That is to install the proprietary drives once booted. I thought they may have some instructions on booting in the trouble shooting link.
I use nomodeset with nVidia, it may now work for you? 

Some find only the generic setting works:
 Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)


[LIST]
[*]Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1
[*]nVidia: nomodeset
[*]Generic: xforcevesa or nouveau.modeset=0
[*]Radeon: radeon.modeset=0
[/LIST]

---

### Post by kkoz83 on 2013-04-21
Thanks for the tip.  I'll try tomorrow.  How do I get a terminal window if I can't get into Ubuntu?

---

### Post by oldfred on 2013-04-21
Sometimes recovery mode will boot, or boot to a command line. But I think the main difference now with recovery mode it that it already has nomodeset. But that is again once installed.

You generally have to add video boot parameters, but some systems require others also.
       [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Check BIOS for settings, sometimes those can make a difference:
and/ or try to boot with acpi=off or nomodeset=0 on the boot line

---

### Post by kkoz83 on 2013-04-21
Thanks, I'll do my best tomorrow or this week.

---

### Post by kkoz83 on 2013-04-23
Okay, this is where I'm at:

I followed the video ([www.youtube.com/watch?v=OTmZYzaxR_k](www.youtube.com/watch?v=OTmZYzaxR_k)) but used "radeon.modeset=0" & got in.  
When I type "additional" into the dash, all I see is user account (I turned Amazon stuff off).

Once I connected to my WIFI, software updater did updates (including Firefox), the asked to restart.  Once restarted, I had to do the radeon.modeset=0 again :(

In the mentioned video, she said about additional drivers.  When I type "additional" all I see is "user accounts".  

How do I check for additional drivers?  Why is my graphics not 100% smooth?

---

### Post by arpanaut on 2013-04-23
Go to System Settings, Under Hardware, you should see Additional Drivers.
You will need to enter your login password.

System Settings are under upper right cog, first item on menu. Or in the launcher on the left.

---

### Post by kkoz83 on 2013-04-23
Okay, thank you, I'll try tomorrow :)

---

### Post by kkoz83 on 2013-04-24
I got it all to work!!! :) :)  I went into software center, typed "additional drivers" in the upper-right box, installed it & ran it.  It found 2 drivers for my AMD graphics card, activated them both, restarted laptop and now all super!!!  Thank you! :)

---

### Post by kkoz83 on 2013-04-24
P.S.  How do I mark this thread as solved?

---

### Post by Elfy on 2013-04-24
> **kkoz83 said:**
> P.S.  How do I mark this thread as solved?

[http://ubuntuforums.org/showthread.php?t=2121377&p=12536730&viewfull=1#post12536730](http://ubuntuforums.org/showthread.php?t=2121377&p=12536730&viewfull=1#post12536730)

---

