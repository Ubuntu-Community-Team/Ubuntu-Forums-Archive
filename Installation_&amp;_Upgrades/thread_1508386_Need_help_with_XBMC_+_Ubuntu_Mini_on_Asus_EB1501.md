---
title: "Need help with XBMC + Ubuntu Mini on Asus EB1501"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by Callah on 2010-06-12
Hello there,

Now i've spent 2 days trying to get these two HOW-TO's to work:

[http://wiki.xbmc.org/index.php?title=HOW-TO_preform_a_Miminal_Ubuntu_and_XBMC_install_on_a_Asus_EeeBox_PC_EB1501](http://wiki.xbmc.org/index.php?title=HOW-TO_preform_a_Miminal_Ubuntu_and_XBMC_install_on_a_Asus_EeeBox_PC_EB1501)

[http://wiki.xbmc.org/?title=Talk:EeeBox-EB1501](http://wiki.xbmc.org/?title=Talk:EeeBox-EB1501)

But i'm not that big of a Linux geek, so now i'm so desperate to find someone who knows how to install it.

   **Here is my steps:**
  1.  Burning "Ubuntu 10.04 "Lucid Lynx" Minimal CD" on my 16GB USB-stick
  2.  Boot from USB
  3.  Select Install, Type username, location and stuff.
  4.  Select "Basic Ubuntu Server" + "OpenSSH Server"
  5.  PROBLEM 1: 
The installer ask me to take my installation out - so i do. But, when i try to boot on the HDD there is just a blinking cursor. If i then try to boot up on the USB-stick - There is Ubuntu.. What tha?
  6.  Login via. SSH as user 'xbmc'
  7.  Running following commands:
  -          sudo apt-get update && sudo apt-get upgrade
  -          sudo apt-get install xbmc xinit x11-xserver-utils -y
  -          sudo apt-get install nvidia-185-kernel-source nvidia-185-modaliases nvidia-glx-185 nvidia-settings libvdpau1 -y
  -          PROBLEM 2: 
sudo nvidia-xconfig -s --no-logo --force-generate --output-xconfig=/etc/X11/xorg.conf 
(Returning: sh: pkg-config: not found)
  -          Try to keep going..
  -          sudo vi /etc/X11/xorg.conf (Inserting stuff..)
  -          PROMBLEM 3: sudo modprobe nvidia 
(Returning: FATAL: Module nvidia not found.)
  -          Try to find log..
  -          grep EE /var/log/Xorg.0.log
  -          (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
  -          (EE) NVIDIA:     system's kernel log for additional error messages.
  -          (EE) Failed to load module "nvidia" (module-specific error, 0)
  -          (EE) No drivers available.
  -          PROBLEM 1 FIXED: I saw that there was some problems between the GRUB kernel, so i did:
  -          sudo apt-get install grub2
  -          sudo upgrade-from-grub-legacy (And choosed the right HDD)
  -          And that fixed it.
  8.  sudo apt-get install wget
  9.  wget [http://nfye.com/EB1501/AlsaUpgrade-1.0.21-4.sh](http://nfye.com/EB1501/AlsaUpgrade-1.0.21-4.sh) -O alsaup.sh
10.chmod +x alsaup.sh
11.sudo ./alsaup.sh -di
12.alsamixer
13.PROBLEM 4: The SPDIF/1 is OFF? 
14.PROBLEM 5: vi /etc/asound.conf (Will create a new file?)

So.. That didn't work.
I need someone who have done it before, and knows how to do it again on a fresh Ubuntu Mini 10.04 with SSH access.
**I'm willing to put a few $$** to the one who can install the drivers and the XBMC so everything works.

Regards,
A sad sad man (Martin).

---

### Post by Callah on 2010-06-13
Bump, anyone - please ?

---

### Post by Purple8 on 2010-12-09
I have exactly the same prob
Followed instructuctions but asks me to reboot before i pick installation.
I cant mount usb drives etc..

---

### Post by Purple8 on 2010-12-09
Hey just found this
[http://humphrey.za.net/2010/07/23/install-ubuntu-10-04-xbmc-on-asus-eeebox-pc-eb1501/#comment-94](http://humphrey.za.net/2010/07/23/install-ubuntu-10-04-xbmc-on-asus-eeebox-pc-eb1501/#comment-94)
USB drives now appaer going to try to get remote working when i get home

---

