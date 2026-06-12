---
title: "Install problem 16.04 - nomodeset partial fix only"
date: 2016-11-13
forum: Installation &amp; Upgrades
---

### Post by Andrew F in Australia on 2016-11-13
Hi All,

I've had a laptop die and bought a Gigabyte P57 laptop to replace it.  It has a Nvidia Card and proprietary driver. 

CPU: Intel 6th Gen. i7-6700HQ 2.6GHz(Turbo 3.5GHz) 64bit
OS:Windows 10
RAM: 8GB DDR4 2133
HDD: 128GB M.2 + 1TB SATA

Graphic: Nvidia GTX 965M Graphics 2GB DDR5 Dedicated VGA
Screen: 17.3&#8221; IPS FHD(1920x1080) LED Screen

*D-Sub *HDMI 2.0 *USB3.0 *DVD Writer*MiniDisplay Port *802.11ac*Bluetooth*Card Reader*USB3.1 Type-C *Dolby Theater*2.9kg




Ubuntu has been my main operating system for the last six years.

The laptop came with Windows 10, but I've had difficulty installing Ubuntu onto this one, have been fighting with it for about 24 hours

The liveCD and a USB (made in windows with Rufus, UEFI/FAT32) both failed to install, hanging on install with an error
NMI Watchdog: BUG: soft lockup - CPU#4 stuck for 22s!

from a google search, I tried changing the grub bootup commands to nomodeset quiet splash.

This allowed the live USB to boot, but the resolution is 600x480 and no cursor is visible or available. Keyboard commands still work, but only half the install screen is visible.

Of course, I've only got Windows here to troubleshoot on - I'm not familiar with the commands

Has anyone had any experience or tips on how to install as dual boot.

I'm looking at running Ubuntu off the 128GB SSD and Windows off a 256GB SSD in the same machine.

[edit post: Turns out this is a known issue with the Intel i7-6700HQ chip and the NVidia GTX960M,965M graphics cards.
 The full solution can be found [from here]("http://askubuntu.com/questions/760934/graphics-issues-after-while-installing-ubuntu-16-04-16-10-with-nvidia-graphics?noredirect=1&lq=1"), correct GRUB boot command would more likely be 

[LIST=1]
[*]Reboot into GRUB. 
[*]Highlight the Ubuntu option and press E. 
[*]Add nouveau.modeset=0 to the end of the line beginning with linux. 
[*]Press F10 to boot. 
[*]Install correct NVidia driver when up and running, by entering
sudo apt-add-repository ppa:graphics-drivers/ppa 
apt-get update
sudo apt-get install nvidia-364 (I used 367)] 
[/LIST]
   
Regards,

AndrewF

---

### Post by Bucky Ball on 2016-11-13
Have a[ look here]("https://ubuntuforums.org/showthread.php?t=2342796&p=13568286&viewfull=1#post13568286").  

You might want to check that thread from the start but the user had what looks like the same, or a very similar, issue to yours and the link I've given is how they fixed. A tweak in the BIOS. It is explained there. 

Hope that helps. ;)

PS: You have Win10 and that would be installed in UEFI. That means you MUST install Ubuntu in UEFI also. Most users here run a dual-boot so yes, plenty of tips to be found here.

---

### Post by Andrew F in Australia on 2016-11-13
Thanks Bucky Ball,

Yes, the stick was formatted UEFI.  I haven't got a lot of options in the BIOS on this - I had a poke around the BIOS. It's pretty minimalistic and all looked OK.

Still hitting my head against the wall on this one.

---

### Post by Bucky Ball on 2016-11-13
Okay, so you can now boot to the options screen where it says 'Try Ubuntu' 'Install Ubuntu' etc.? If so, 'Try Ubuntu' and when it gets to the half a screen or whatever, see if you can somehow manage to get to 'Display' and choose a different resolution. 

You can then locate the 'Install Ubuntu' icon on the desktop and install. Let us know how you go.

---

### Post by Andrew F in Australia on 2016-11-13
Thanks BB - 

I managed to install using keyboard commands only off the screen, randomly tabbing and hoping I hit 'next' - boots into Linux OK now.

The Elan touch pad isn't recognised (in xinput, and is unresponsive) and the NMI watchdog error now occurs on shutdown.  Manageable errors - I'll google a bit and see if I can fix it first before I ask for help.  Typing this and using Linux with keyboard only. Been years since I've had to use all shortcuts.

Thanks for your help.

---

### Post by Bucky Ball on 2016-11-13
No problems, but if you have installed, you should update and go to 'Additional Drivers' and install the NVidia driver there for the card. It should be the 361 or the 367. That may fix up a few things. If you haven't installed the NVidia driver you are running on the open-source nouveau driver which is fine for some but not others.

You should be trying the NVidia driver. ;)

Thanks for marking the thread as solved. Enjoy.

---

### Post by Andrew F in Australia on 2016-11-13
Edit post: SOLVED - NMI Watchdog: BUG: soft lockup - CPU#4 stuck for 22s so this answer comes up in a google search

Hi BB and thanks for all your help,

Strangely enough, late last night I came across[ this thread]("https://ubuntuforums.org/showthread.php?t=2328033&p=13505451#post13505451") which said there's a known conflict between the intel i7-6700HQ chip, the NVidia GTX96xM graphics card and the Linux kernel that causes the NMI Watchdog: Bug hangs..

Simple fix was to install the correct proprietary driver (through the repositories) and all was solved - no more hang, smooth startup and shutdowns (especially off a SSD, first time I've used one.)

Regards,

Andrew F

---

