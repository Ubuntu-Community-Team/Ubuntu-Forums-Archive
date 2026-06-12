---
title: "Trying to Dual Boot Windows 7 / Ubuntu 10.04"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by hexbomber on 2010-08-12
I am trying to setup dualboot between Windows 7 and Ubuntu 10.04 on my new system.

I have partitioned off a 1.5 TB drive, and given 500GB to Windows 7, I have another 500GB drive in the machine that I am using entirely for Ubuntu.

I have Windows 7 installed correctly, and it boots/runs fine, then when I go to install Ubuntu, the install completes "successfully", but will not boot. 

The first time this happened there was a flashing cursor that loaded in the top-left corner of a black screen instead of showing grub.

This second time around, the same thing happened. During the install, Ubuntu found Windows 7 Loader and added it to the grub menu.

I have tried using the super grub disk to find/resolve the issue, and when I boot using the super grub disk it displays a grub menu for me, and i can make my choice of OS.

If I choose Windows 7, everything loads fine, however if I choose Ubuntu from the menu, then everything goes black. My monitors turn off (not getting any signal), and I can't tell what's going on.

I am using the alternate install cd (have tried x86 and x64), and am installing Ubuntu using the Full Disk Encryption option.

I have run integrity checks on the install disks, and the memory check on my system, both have passed.

This post has been pretty long winded, and it was typed from my cellphone so please forgive any spelling/grammatical mistakes.

I appreciate any insight/help on this :).

Thanks in advance!
- Hexy

---

### Post by Elmer Fudd on 2010-08-12
Were you able to run/test from a LiveCD before you tried the install?
Some details about your hardware please.

---

### Post by MAFoElffen on 2010-08-12
> **hexbomber said:**
> I am trying to setup dualboot between Windows 7 and Ubuntu 10.04 on my new system.

I have partitioned off a 1.5 TB drive, and given 500GB to Windows 7, I have another 500GB drive in the machine that I am using entirely for Ubuntu.

I have Windows 7 installed correctly, and it boots/runs fine, then when I go to install Ubuntu, the install completes "successfully", but will not boot. 

The first time this happened there was a flashing cursor that loaded in the top-left corner of a black screen instead of showing grub.

This second time around, the same thing happened. During the install, Ubuntu found Windows 7 Loader and added it to the grub menu.

I have tried using the super grub disk to find/resolve the issue, and when I boot using the super grub disk it displays a grub menu for me, and i can make my choice of OS.

If I choose Windows 7, everything loads fine, however if I choose Ubuntu from the menu, then everything goes black. [COLOR=Red]My monitors[/COLOR] turn off (not getting any signal), and I can't tell what's going on.

I am using the alternate install cd (have tried x86 and x64), and am installing Ubuntu using the Full Disk Encryption option.

I have run integrity checks on the install disks, and the memory check on my system, both have passed.

This post has been pretty long winded, and it was typed from my cellphone so please forgive any spelling/grammatical mistakes.

I appreciate any insight/help on this :).

Thanks in advance!
- Hexy
I second "Elmer Fudd" on the detail on your hardware (especially video) and if you were able to run 10.04 from the LiveCD.  

--> I see a few things already from your first post (see [COLOR=Red]red[/COLOR] highlight)... That was correct right?

---

### Post by hexbomber on 2010-08-13
My hardware is currently:

Asus M4A88TD-V (EVO) Motherboard (HDMI, USB3.0 Version)
2 x 2GB DDR3 G.Skill 1066Mhz RAM
1 x 1.5 TB Western Digital (Cavier Green, 5400 RPM HDD [Windows Partition of 500 GB and the rest is a NTFS partition])
1 x 500 GB Western Digital (Cavier Black, 7200 RPM HDD [UBUNTU])
2 x nVidia 8400 GT Graphics Cards (Made by XFX)

For monitors I have 3 x 19" Acer x193w LCD's and one 17" Dell LCD.

I have used these video cards on other ubuntu setups, and have run the LiveCD, all works fine in the live CD.

---

### Post by Elmer Fudd on 2010-08-13
Is the liveCD that works a 32bit or 64bit Ubuntu and did you try to install from that CD?

---

### Post by MAFoElffen on 2010-08-13
I also have 2 bridged XFX NVidia 6800GT Ultra SLI cards... In Ubuntu 10.04, the Ubuntu generic video driver doesn't like two instances of the same card. But the NVidia Driver (from Nvidia) does. Same goes for the Ubuntu 10.04 Server Edition....  The 10.04 LiveCD doesn't run in a graphics mode with two bridged SLI's either, until I pull one of my cards.  (IT will run the install with both...)

It's an easy fix with a few minutes patience.  Here's the workaround I came up with to get around it on mine...  
- Make sure the computer is shut down and unplug the power cable.  
- Remove the bridge cable and your secondary SLI card.  
- plug your power back in
- Boot up into your Bios and save the settings.  
- Boot up into Ubuntu.  (It will boot up fine in Graphics mode with the single card.)
- Goto System>Adminstration>Hardware Drivers
  > It will find your NVidia Card
  > Install the NVdia driver.
 <>Or go to NVidia and download/install it it...
- Start up a terminal session and type ```
sudo nvidia-xconfig
```- Shut down Ubuntu  
-Unplug your power
- Put your secondary SLI card back in and reconnect the SLI Bridge cable.
- reconnect your power cable.
- Boot into your BIOS and save the settings.
- Boot into Ubuntu... and it should be fine.
- The NVidia Xserver Settings will then be under the System>Administration... to do any tweeking and configuring your montiors...

---

### Post by hexbomber on 2010-08-13
I have tried both 64 and 32 bit live cd's (both work).

I am not using SLI for the cards, I just have two independant cards, no bridges or anything. The problem is not a graphics problem, since the LiveCD works fine (I can't install from the LiveCD since the ubuntu installation disk with full disk encryption is the alternate-text based installer, there is no LiveCD function on it).

If it was a graphics problem I'd assume that by Ctrl-Alt-F1'ing I could get to a tty prompt and then at least figure some stuff out command line which is not the case.

The problem seems to be a grub problem. For some reason when I try installing Ubuntu after installing Windows 7, it sees Windows 7, but does not setup Grub properly to boot between the two.

---

### Post by MAFoElffen on 2010-08-13
> **hexbomber said:**
> (Edited)
I have tried both 64 and 32 bit live cd's (both work).

I am not using SLI for the cards....The problem is not a graphics problem...

It is "a graphics problem," even for TTY.  Early on when I was testing the 10.04 alpha's and betas, this problem came up... and has not been resolved with 10.10 apha3 yet... but they're working on it.

"On mine," it didn't matter if I was using SLI either...  It's not a problem of the driver "not doing SLI"... It's a problem of the driver locking up because it's confused with multiple instances of the same card and/or with multiple cards.

An easy way to check would be to pull one of your cards and try to boot up. (or to do a "nomodeset" which doesn't "always" work)

For example Ubuntu 10,04 LTS Server is not a graphics based OS... It's displlay mode is TTY only.  If I have both of my cards in, with or without the bridge cable (tested it both ways), it locks up my machine on the video in TTY mode. For me to boot up at the initial install of the Server Edition, I pull one of my cards and it comes up fine.  I reported it as a bug, but the server platform community doesn't see that as a "problem"... they felt that "high-end graphics are not needed for a server platform" and that anyone would be crazy to use a high-end graphics machine as  server platform.  I felt it was a compatibility problem that should be noted to perspective users....  It is a reported Bug in the Desktop Edition.

The point there is that the Server Edition is based on the Desktop Edition and they share the same graphics problems with that.  A lot of the time, I run without being SLI-bridged.  I "have" multiple monitors to run Virtual Machines for testing- with the Virtual Machine coming up on another montior... or using one to doing debugging on.  I configure my monitors through the NVidia Xserver.

Another thing that you could do (as mentioned before) is to edit the GRUB menu as outlined here: [[FONT=Arial][SIZE=2] Ubuntu 10.04 “Lucid” Blank Screen at Startup : Workaround[/SIZE][/FONT]]("http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/") to see if that will get you up.  I was going to see how they affected "multiple" video cards later today in "different" modes.    So far the nomodeset works until you can get nvidia-xconfig, but the xforcevesa doesn't.  NVidia cards really don't like the vesa modes... I ran into this with previous upstream xorg changes in OpenSolaris also...  (worked out now)

It will be different for 10.10 (hopefully) as there's already changes in these new snapshots where we're trying different things because of the current changes in in Xorg and desktop...  With multiple NVidia carrds we're still using the nomodeset on the LiveCD and the nvidia-xconfig and Nvidia Xserver thereafter.  (reference: [SIZE=1]WARNING: X-server breakage coming soon to a computer near you)[/SIZE]

---

### Post by hexbomber on 2010-08-13
So I pulled out all the harddrives except for one 40gb sata, and installed Ubuntu 10.04 (64 bit) and everything worked fine.

I did the exact same process as before, full-disk encryption, the whole 9 yards, and it found everything and started up fine. Graphics ran fine, compiz looks really nice.

Now I just have to find a way to reinstall 10.04 on my actual 300 GB partition and get grub to play nicely.

---

### Post by MAFoElffen on 2010-08-13
> **hexbomber said:**
> So I pulled out all the harddrives except for one 40gb sata, and installed Ubuntu 10.04 (64 bit) and everything worked fine.

I did the exact same process as before, full-disk encryption, the whole 9 yards, and it found everything and started up fine. Graphics ran fine, compiz looks really nice.

Now I just have to find a way to reinstall 10.04 on my actual 300 GB partition and get grub to play nicely.
Good Job!!!  (Sorry if I got sidetracked...)

One idea might be to install all your drives again; Copy the 40GB to the 300GB partion; unmount the 40GB drive for backup/grub reference; start up on a SuperGrub disk to find the 300GB system and get into it/making your grub changes; then run grub-config to find Win7. Grub boot is still installed on that disk right?  (the one with the 300GB partition)

---

### Post by hexbomber on 2010-08-13
I will play with moving the files between the harddrives tomorrow and post back with the details :).

Thanks everyone.

---

### Post by Elmer Fudd on 2010-08-13
Glad to check back in an see you are making progress.

Even if they are not now, were any of the drives or the computer set up with RAID?

---

### Post by hexbomber on 2010-08-14
Nope, none of the drives were in RAID.

---

### Post by Elmer Fudd on 2010-08-14
With you hardware in the original configuration, did you ever try to install 32bit non-encrypted 10.04- just to see if that worked?

---

