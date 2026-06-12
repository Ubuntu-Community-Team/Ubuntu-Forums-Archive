---
title: "Issues installing Ubuntu on new hardware (16.04)"
date: 2016-07-27
forum: Installation &amp; Upgrades
---

### Post by cystalis on 2016-07-27
Hello

[COLOR=#000000][FONT=Verdana]So I just purchased some new hardware to build a 4k ready HTPC. I've got an Skylake i3 6100T (35W) CPU, 8GB or DDR4 ram, a 240GB SSD and 2TB HDD, and a GTX 960 GPU. 

[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]I tried manually installing Ubuntu 16.04, but it keeps crashing on logon. Everything seems to go through ok, and on reboot and login the screen takes a while to switch to the default background then I either get an error window that pops up, and then quickly goes away (over and over) or nothing. 


[/FONT][/COLOR]

---

### Post by gordintoronto on 2016-07-27
You might consider pulling the GTX 960 and install with just the Intel graphics. You might find that it's completely up to the job.

Or you could read up on "nomodeset".

When you say "manually installing Ubuntu," I assume you meant that you booted from a flash drive or DVD and selected "install"?

Motherboard?

I'm not sure why you would choose Ubuntu for an HTPC, rather than, for example, Xubuntu.

---

### Post by oldfred on 2016-07-27
With Skylake you have enough video horsepower to run HDTV. 

My Haswell Dell system was purchased for the same reason and uses only Intel video. But I ended up just using it to watch Comcast DVR recordings on my DVR in Illinois while in Florida. But only Windows works for that, so far.

Most have to use nomodeset to boot in lower quality graphics so they can install the nVidia driver.
If you install one nVidia driver but want or need a different one, you must totally purge first or you get major conflicts. And only install from Ubuntu repository or add ppa to install the very newest driver from nVidia if needed.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Or if you can boot recovery mode to a terminal:

 # list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices
# or
ubuntu-drivers devices | grep recommended  
   sudo apt-get remove --purge nvidia-*
sudo ubuntu-drivers devices
sudo ubuntu-drivers autoinstall 

      
 # Shows standard repository versions
ubuntu-drivers devices
sudo apt-add-repository ppa:graphics-drivers/ppa
# should show newest versions available in addition
ubuntu-drivers devices 
You can then choose which to install or the auto install option as above.

One user connected to Intel video port and installed Ubuntu and nVidia driver. Then reconnected to nVidia video port.
But some Intel video also require boot parameters, like the nomodeset.

---

### Post by cystalis on 2016-07-28
Hi Everyone.

Thank you for the replies. I actually got everything working. First off, I plan on using the HTPC for arcade emulation, 4K@60Hz video playback, which is why I got the GTX 960, it has a HDMI 2.0 port, and supports 4K@60Hz, and also run some 3D games from Steam.

So this is what I did to resolve my issue:


[COLOR=#000000][FONT=Verdana]After some digging around on the internet it sounded like the nouveau open source drivers that ubuntu 16.04 has built in was causing the crashing.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]So what I ended up doing was, removed my GTX 960 and used the built in iGPU. Installed ubuntu as normal. Installed the Close source Nvidia drivers (637.27) from repository, removed the nouveau drivers. Shutdown. Re-installed the GTX 960, disabled the iGPU in bios. [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I was able to log into UBUNTU no issues. Nvidia drivers see the 960, and Kodi sees it to. All good to go![/FONT][/COLOR]

---

