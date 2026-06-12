---
title: "Ubuntu 10.04 Live CD cant try/install -&gt; blank screen"
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by sag0th on 2010-07-22
Hello all
I have an issue with Ubuntu 10.04 Live CD which is driving me crazy for the last 4 days. After choosing try/install option from Live CD the installation is stuck after some time and screen just goes blank.
When I remove "quiet" and "splash" from bootargs the last message I see is "Setting sensor limist [OK]".

I have tried every option that was suggested in the forums: noapic, acpi=off, nomodeset, xforcevesa, radeon.mode=1/0...
Actually the only way I can start try/install without getting some screen crap (purple mess) is with "nomodeset".

PC is:
Athlon64 X2 5400+
Asus M2V-MX moboard
2+1GB DDR2 800
GeCube  Radeon x800GTO
500GB WDigital SATA2 HDD

There should be workaround.
I don't want to go back to windows... :(

---

### Post by dstew on 2010-07-22
Assuming the Live CD is OK (does it work in other computers?), the most likely problem is that the Live CD installer kernel has some hardware incompatibility issues with your system. To install, try the Alternate Install CD. It installs the same Ubuntu desktop, but uses a text-based installer that works more reliably in many systems. You can find the Alternate Install CD image on the [Lucid Release page]("http://releases.ubuntu.com/lucid/").

---

### Post by varunendra on 2010-07-23
> **dstew said:**
> Assuming the Live CD is OK (does it work in other computers?), the most likely problem is that the Live CD installer kernel has some hardware incompatibility issues with your system. To install, try the Alternate Install CD. It installs the same Ubuntu desktop, but uses a text-based installer that works more reliably in many systems. You can find the Alternate Install CD image on the [Lucid Release page]("http://releases.ubuntu.com/lucid/").

+1.
Or get 'back' to Karmik (9.10), better than returning back to windows :D. Karmik has almost no issues with graphics.

---

### Post by sag0th on 2010-07-23
I'll try but are you sure it's graphics related?

---

### Post by varunendra on 2010-07-23
Not sure, but this is most often the case (mostly with ATI graphics, which is yours).
Btw, trying a live cd with different kernel &/or graphic driver versions is the excellent way to verify this.

---

### Post by ttahola on 2010-08-13
Hi,

I have a similar issue. Based on googling this seems to be graphics card related. Although I tried to use a USB memory stick for installation. I have a Radeon 5450 and BenQ 24" plugged in to the HDMI port. I was going to complain that this use case (installation) should work out-of-the-box on most of the modern computers. But then I realized that I have not done much to help fixing the issue.

So for now, I will move on to some other Linux distro. I'm not able to debug or fix issues like this at the moment; I just would like to try things out as easily as possible. This really was a disappointment :( Last time I tried ubuntu I was at least able to install it easily. It was a few years ago on a computer with another Radeon graphics card (9250).

+Tero

---

### Post by ttahola on 2010-08-13
Hi,

I have a similar issue. Based on googling this seems to be  graphics card related. Although I tried to use a USB memory stick for  installation. I have a Radeon 5450 and BenQ 24" plugged in to the HDMI  port. I was going to complain that this use case (installation) should  work out-of-the-box on most of the modern computers. But then I realized  that I have not done much to help fixing the issue.

So for now, I  will move on to some other Linux distro. I'm not able to debug or fix  issues like this at the moment; I just would like to try things out as  easily as possible. This really was a disappointment :( Last time I  tried ubuntu I was at least able to install it easily. It was a few  years ago on a computer with another Radeon graphics card (9250).

+Tero

---

### Post by f6e9a on 2010-08-13
i had the black screen too after the ubuntu dot screen 
i used the "i915.modeset=1"
and that fixed it but on each boot i have to edit grub

---

### Post by claracc on 2010-08-14
> i had the black screen too after the ubuntu dot screen
i used the "i915.modeset=1"
and that fixed it but on each boot i have to edit grub 

It seems that you need to do the change permanent as it is indicated in this thread: [http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

   1. Edit the /etc/default/grub file. You will need Admin privileges to do so (sudo)
   2. Find this line: GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”
   3. Replace with: GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash <option>”

For example, if I had an older Intel model, my GRUB configuration would read:

    GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash i915.modeset=1&#8243;

Save your changes and you should get proper graphics on each reboot.

UPDATE: Based on a lot of user feedback I am reminded that you need to run ‘update-grub’ after you make changes.

---

### Post by ttahola on 2010-08-14
I was able to overcome the issue by switching to Linux Mint. I have understood that it is based on Ubuntu. The difference is that Mint had this option to start in safe mode in the boot menu. I first tried to start in normal mode, but the end result was the same as with Ubuntu installer: screen goes off after loading phase, i.e. after the loader animation with "dots" is done. Then I tried the safe mode and Mint started successfully and I was able to install. Also the graphics worked ok from the first boot after the installation. I'm impressed! I hope the graphics issues with Ubuntu installer will be fixed.

---

### Post by ttahola on 2010-09-05
Ok, now I finally got some time to try this again. Here is how I got Ubuntu 10.04 installed and working:

[LIST=1]
[*]Created an installation CD with the alternate ubuntu desktop installer i.e. "ubuntu-10.04.1-alternate-i386.iso" (the alternate version uses text mode instead of any fancy graphics so this bypasses the graphics issues with the default installer)
[*]Install
[*]Boot to "recovery" mode (grub boot menu option 2)
[LIST]
[*]you should now see a text based menu with several startup options
[/LIST]
[*]Select "console with network support" or something like that
[*]Copy the failsafe xorg configuration as the default configuration:
[LIST=1]
[*]cd /etc/X11/
[*]cp xorg.conf.failsafe xorg.conf
[LIST]
[*]Note that there was no default xorg.conf available in my system, so this did not overwrite any existing setting. You may want to create a backup copy, if you do have a default xorg.conf available.
[/LIST]
 
[/LIST]
 
[*]Reboot and start Ubuntu (into the default, non-failsafe mode)
[*]Voilá! Ubuntu login screen is shown instead of a black screen! The screen resolution is 1280x1024 and no other resolutions are available (because you are using failsafe xorg.conf settings)
[*]Install ATI drivers (xserver-xorg-video-radeon or something if I remember right)
[*]Configure ATI drivers
[LIST=1]
[*]open a terminal window
[*]"sudo aticonfig --initial"
[/LIST]
 
[*]Reboot
[*]Ubuntu starts with the monitor's native resolution. Yeah baby!
[/LIST]
To find out these steps, I also tried dozens of others that did not help. Including the before mentioned grub configurations. Also, the failsafe startup option did not work on my computer for some reason (after step 3 above). There was some issue with the keyboard config, I think.

My computer is a Dell Inspiron with Intel i3, ATI RadeOn 5450, 4 GB memory, 640 MB HDD, BenQ24" plugged into the HDMI port of the RadeOn, Dell's USB keyboard, ...

---

