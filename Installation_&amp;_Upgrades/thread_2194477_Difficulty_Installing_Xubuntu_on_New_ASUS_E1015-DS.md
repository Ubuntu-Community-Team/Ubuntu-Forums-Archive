---
title: "Difficulty Installing Xubuntu on New ASUS E1015-DS03"
date: 2013-12-18
forum: Installation &amp; Upgrades
---

### Post by mrmojopc on 2013-12-18
Hi, all! I'm new to the forums, althugh I've been an Ubuntu/Xubuntu/Lubuntu user for awhile.

I just got a new Asus E1015-DS03 through Amazon, preloaded with Ubuntu 12.04 LTS 64-bit. It's a "cute" 10" laptop with a 320 GB HDD and 2 GB RAM. Although Ubuntu is alright (I love the dash, but that's about it), I prefer Xubuntu, and having installed it before on different laptops, I didn't foresee any problems. Unfortunately, it hasn't worked according to plan, and I really need help to understand what I'm doing "wrong".

I downloaded Xubuntu 12.04 64-bit version and used UUI installer program to load the installer onto a USB drive. When I booted the machine, I pressed F2 to enter setup options to change my boot options to the USB drive. Here's where it got interesting. It uses UEFI instead of the old-school BIOS I'm used to. The USB drive shows up as a boot option as two separate entities: a UEFI entry (UEFI: Xubuntu...) and regular (Xubuntu...).

When I set the order to UEFI USB, save, and reboot, I get a boot menu to either try Xubuntu, install Xubuntu, or run diagnostics on the HDD. After selecting the Try choice, it showed the Xubuntu splash screen with the progress bar, then it left me at an Ubuntu login (orange-y background), demanding a username and password. It won't take the username and password I initially had set up, and I don't know of any other combinations to try (user? guest?). So I chose to restart the machine, but it didn't do anything when I selected Restart or Shut Down. I had to hard-shutdown and start over. Tried that a few times; same result.

I then chose the non-UEFI version of Xubuntu for first boot option in setup. That option led me to a recovery screen to recover my installation, only with an error that read, "This option is only availale for Ubuntu systems". The Back and Continue buttons of the dialog box didn't do anything; only the Quit option worked. Tried that a couple of times; same result.

When I (temporarily) gave up and went to do a normal boot into Ubuntu, I got the GRUB screen. Now, I hadn't seen that before I tried all this (it always just boted straightaway to my Ubuntu desktop). (I had removed the USB drive before booting. It booted into Ubuntu okay, so I reckon no long-term damage was done.

However, I am left with the puzzle of how to install Xubuntu on a new laptop with UEFI and some weird parttioning Asus did (I think they put a recovery option if you hit F9 on startup) on the HDD. I am always thirsty for more knowledge, but there isn't a lot of useful tech information on this machine.
I would appreciate any insight passed my way. (BTW, being new here, I don't want to overstep my bounds, but I'm not interested in trying other distros or learning to "live with Ubuntu". I know that what I want to do can be done; I just don't know how.)

Thank you.

---

### Post by ubfan1 on 2013-12-18
Did you try the username "ubuntu" with a blank password?  Sometimes that pops up, not sure what triggers it.

---

### Post by mrmojopc on 2013-12-18
Edit: Thanks, but I tried that (ubuntu/blank password; blank username, ubuntu password; ubuntu username, ubuntu password). No go.

---

