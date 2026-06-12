---
title: "login loop on Ubuntu 15.10"
date: 2016-01-04
forum: Installation &amp; Upgrades
---

### Post by Patrick_Wright on 2016-01-04
[FONT=arial]I recently purchased a new (2015) Toshiba Satellite S50-C, wiped Windows 10, and have been attempting to install Ubuntu for several days.
Details on the machine:
[COLOR=#333333]Intel Core i7-6500U Processor (4M Cache, 2.50 GHz) with Intel Turbo Boost Technology 2.0 (x64-based processor) 16 GB DDR3L 1600MHz = 8GB + 8GB 1.0TB (5400rpm); Hybrid 8G Serial ATA hard disk drive 256GB M.2 Solid State Drive (SSD); 4GB DDR3 NVIDIA GeForce FTX 950M with NVIDIA Optimus Technology; 15.6" FHD TruBrite display (1920x1080)

[/COLOR]I am attempting to install Ubuntu on the 256 GB SSD.

[COLOR=#333333]After failing to get 14.04 to install (usually some problem with failing to boot or freezing), I decided to go with 15.10 since my hardware is so new.[/COLOR]
[COLOR=#333333]I have completed a 15.10 install via thumb drive, in CSM boot mode (not UEFI), and with the Intel Turbo Boost Technology disabled. I then re-enabled the Turbo boost after install.[/COLOR]

[COLOR=#333333]Now, I am unable to proceed past the login screen. It goes black, flashes a purple screen, and then returns to the login screen. Guest login also does not work.[/COLOR]

[COLOR=#333333]CTRL + ALT + F1 (or F2, F3) do not work to get me in a terminal. If I enter the GRUB edit screen (typing 'e') in startup when GRUB is displayed, I can access a terminal by adding '3' at the end of the linux line (runlevel 3). Also, at the recommendation of add'l posts, I have added the following to the same line in GRUB:[/COLOR]
[COLOR=#333333]replace 'quiet splash' with 'nomodeset'[/COLOR]
[COLOR=#333333]i915.modeset=0[/COLOR]
[COLOR=#333333]i915.i915_enable_rc6=1[/COLOR]
[COLOR=#333333]nouveau.blacklist=1[/COLOR]

[COLOR=#333333]I am not sure if any of the above is necessary.... I originally added 'nomodeset' because I was booting into a black screen. This seems to have solved that issue, but has created the login loop issue.

[/COLOR]I have a feeling this is related to the NVIDIA driver. In a previous successful login, the graphics were incredibly slow, but I was able to change the driver (via 'additional drivers' GUI) from Nouveau to NVIDIA proprietary.
Running dkms status gives:
bbswitch, 0.7, 4.2.0-22-generic, x86_64: installed
nvidia-352, 352.63, 4.2.0-22-generic, x86_64: installed

Also, I have read that permissions with .Xauthority can be a common problem, however, when I run ls -lah, I have:
-rw------- 1 pwright pwright     54 Jan   4 12:37 .Xauthority

Any advice would be greatly appreciated!!
--PW[/FONT]

---

### Post by ubfan1 on 2016-01-04
Skylake needs this (15.04...):
i915.preliminary_hw_support=1
Other things to try:
To slow SSDs to allow them to boot:
libata.force=noncq
or
intel_idle.max_cstate=1 

Definitely try the newest release for your hardware, or even a 16 alpha/beta if nothing else works.

---

### Post by Patrick_Wright on 2016-01-05
I'm assuming you mean to insert these arguments with the others on the same line?
(that is, GRUB_CMDLINE_LINUX_DEFAULT=".....")

---

### Post by Patrick_Wright on 2016-01-08
Please see the post here for updates to this problem, or to provide further feedback:
[http://askubuntu.com/questions/716942/login-loop-on-ubuntu-15-10](http://askubuntu.com/questions/716942/login-loop-on-ubuntu-15-10)
I am still struggling to have a successfully booting and operating system!

---

### Post by ubfan1 on 2016-01-08
You can just edit the options onto the kernel line from the grub menu, type "e" and follow bottom-of-the-screen directions.  I'd try one option at a time, but if you have the nvidia driver installed, maybe some leftover config, like "nomodeset" is clobbering it.  Look in /etc/modprobe.d for any file with any of the nomodeset options.  and comment it out or remove the file.  Is you BIOS/firmware up-to-date?  There have been reported problems with video issues without CMS ([http://askubuntu.com/questions/718198/ubuntu-live-usb-wont-start-with-csm-disabled](http://askubuntu.com/questions/718198/ubuntu-live-usb-wont-start-with-csm-disabled)).  Maybe look at the various driver loads in the startup logs   dmesg |egrep -i "vga|noveau|nvidia"

---

