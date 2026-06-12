---
title: "How to install display driver when no display?"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by XEyedBear on 2010-02-16
[B]I'm trying to recover gtom a surprising defect in Ubuntu 9.10 where  it has apparenlty installed completely but boots to a 100% blank, black  screen. Thinking that a display driver update is necessary, I find this  at the Nvidia web-site:
  
STEP 3:[/B] Install 
Type "sh NVIDIA-Linux-x86-1.0-7182-pkg1.run"  to install the driver,  then edit your X config file as appropriate. If  you are using a Linux 2.6 based system, type "modprobe -q 
agpgart",  first. See the text [README]("http://download.nvidia.com/XFree86/Linux-x86/1.0-7182/README/readme.txt")  for more detailed instructions.

This raises the follwing questions:

1. Where, exactly, should I type this on a completely blank screen, with  no cursor visible?
2. What exactly is an X config file and how would I find one to edit?
3. What does 'appropriate' mean and to whom, or under what conditions,  is this appropriateness meant to apply?
4. How would I know if if 'if'clause about Linux 2.6 based system  applies?

Some assistance would be greatly appreciated.

 - how do I exit the 'X-system' as Nvidia requires?
 - how do I change the 'runlevel' and what should it be changed to ?

 Have temporairily borrowed an ATI card from another system, I can boot into Ubuntu and am trying (with zero success so far) to installl the correct Nvidia driver.I have found out how to exit the X-system, but I have run across many other problems. the advice in [http://ubuntuguide.org/wiki/Ubuntu:Karmic#Installation_of_ATI_and_nVidia_Graphics_drivers](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Installation_of_ATI_and_nVidia_Graphics_drivers) is erroneous:
 -   there is no xorg.conf file in /etc/X11 on my system
-  the advice causes me to download the wrong nvidia driver - it is not in accord witht the advice given by nvidia
- even if I download the corrrect driver, the 'sh' command fails with 15 errors, mostly of the form "cannot open meta: No such file"
-  trying to edit /etc/init/rc-sysinit.conf to change the run level fails because I do not have permission to save over a read-only file when using gedit.
 - I have no idea what run-level I should use (it's currently 2, so I am guessing at 1)
 -
All in all this seems like very hard work to install Ubuntu. I have been working at it for more than 30 hours now (and that's not elapsed time). I would have thought the process had been more thoroughly tested than this.....

---

### Post by oldos2er on 2010-02-16
Which Nvidia card do you have? When you installed 9.10, it should've installed open source drivers for your card, with the option for you to update to proprietary drivers once the install's complete. An xorg.conf file is no longer created by default.

If you can boot to recovery mode, run the command ```
apt-get update && apt-get install xserver-xorg-video-nv
```

Obviously you'll need to remove the ATI card first.

---

### Post by XEyedBear on 2010-02-17
> **oldos2er said:**
> Which Nvidia card do you have? When you installed 9.10, it should've installed open source drivers for your card, with the option for you to update to proprietary drivers once the install's complete. An xorg.conf file is no longer created by default.

If you can boot to recovery mode, run the command ```
apt-get update && apt-get install xserver-xorg-video-nv
```Obviously you'll need to remove the ATI card first.

Aye, therein lies the rub. If I remove the Ati card then the system boots to a totally blank screen. You are confirming that I cannot install the necessary nVidia driver with the Ati card installed? Not even if I set the system to base vga (640 x 480) mode? Or how about in 'text' mode (as in after I exit from the X system)?

How would I boot to recovery mode?

The nVidia card I would like to use is a Riva TNT2 M64. Nvidia has a clearly identified driver for it on their web-site. This is not the one which the guide I referenced in my previous append would download.



This whole process, togther with an entry in your profile, reminds me of the 100's of hours I spent in the early 80s trying to get OS/2 1.0 working on various then unannounced display hardware. All that seems to have changed is the amount of memory, CPU cycles, DASD involved. The elapsed time is still the same. (installing from 13 or 14 diskettes took about as long then as it does today with a high speed ATAPI drive. Or maybe I work a lot slower now then I did then....)

---

### Post by 3rdalbum on 2010-02-17
This shouldn't happen. Probably part of the reason why it's happening is because nobody who tested Ubuntu 9.10 has access to such an ancient graphics card. (ffr, it would have helped if you'd mentioned in this post that you have a TNT graphics card, some people won't look at your older posts).

First, run ALL pending updates. This might possibly fix your problem anyway, but you'll need to do this. Now use Synaptic Package Manager to install the "linux-generic-headers" and "build-essential" packages.

[http://www.nvidia.com/object/linux_display_ia32_71.86.13.html](http://www.nvidia.com/object/linux_display_ia32_71.86.13.html)

is the URL where you can download the graphics driver.

Put the driver on your desktop. Log out. Press Control-Alt-F2 to switch to a virtual terminal - you can now log in to this.

Put in the following:

```
sudo killall gdm
cd Desktop
sudo sh NVIDIA-Linux-x86-71.86.13-pkg1.run

```

This should begin the process of asking you questions and installing the driver. Just answer "yes" to everything.

When you reboot, you should have the proprietary graphics driver installed and enabled... I hope Nvidia's driver installer doesn't refuse to run if it doesn't detect an Nvidia card.

What I would check is that the graphics card is actually working anyway, and if it is, please file a bug report against the "xserver-xorg-video-nv" package at [www.launchpad.net](www.launchpad.net).

---

### Post by presence1960 on 2010-02-17
If you are certain the Nvidia card works remove the ati card and put the Nvidia card in. Boot your machine and at the GRUB menu choose Recovery Mode. Then choose netroot. You can install envyng from there. Type the following one at a time

```
apt-get install envyng-core
apt-get install envyng-qt
apt-get install envyng-gtk
```

When above are installed run ```
envyng -t
```Follow the prompts to install the Nvidia driver. When completed reboot.

---

### Post by XEyedBear on 2010-02-17
Oh, there's no doubt this card works: I can install Win2k on this system in about 40 minutes and be up and running with Office 2003 in an hour. There's also enough resources to do some reasonable editing on a smallish jpg in Photoshop (say less then 5 MB jpeg). I can watch movies too. I think that's enough of a valid test.


It's clear that there are different interprations of what a 'blank screen' means. By blank, I mean 'nothing, nada, black, like the monitor is off'. Given my, admitedly picky, definition of 'blank', I don't know whwre I am going to select any options from the GRUB menu, which I cannot see, because the screen is blank

---

### Post by presence1960 on 2010-02-17
Sorry I didn't realize you didn't even get the GRUB menu.

---

### Post by oldos2er on 2010-02-17
You boot into recovery mode by choosing the recovery kernel option in the grub menu.

I think you'd be better off using Puppy Linux, or another distro that better supports older hardware.

---

### Post by XEyedBear on 2010-02-17
> **3rdalbum said:**
> Now use Synaptic Package Manager to install the "linux-generic-headers" and "build-essential" packages.


Synaptic package manager can find no packaes with the name 'linux-generic-headers'.

There are about 20 packages with a name like 'linux-headers-generic', most appear to have the same description but different version numbers. Which of these should I install?

Synaptic package manager can find no packages with the name  'build-essential'.

Are we talking about the same version of Ubuntu? I am trying to install the version 9.10.

---

### Post by XEyedBear on 2010-02-17
> **oldos2er said:**
> You boot into recovery mode by choosing the recovery kernel option in the grub menu.



I'm a bit lost with thid advice: blank screen = a screen which is blank No 'pixels' on, let alone a menu, of any kind.

---

### Post by oldos2er on 2010-02-17
Assuming Ubuntu is the only OS installed on this computer, hold down a Shift key after the BIOS has loaded, and you should see a grub menu.

 Aside from video cards, what are the system's specs?

---

### Post by XEyedBear on 2010-02-18
> **oldos2er said:**
> Assuming Ubuntu is the only OS installed on this computer, hold down a Shift key after the BIOS has loaded, and you should see a grub menu.

 Aside from video cards, what are the system's specs?

Thanks for this tip. Now I will try your previous advice - except that I have proceeded as follows: 

I have made a totally clean install, having first deleted all partitions using a Win 2K install CD. The new install is on the basis of a borrowed Ati card (incidentally just as old as the nVidia card I want to use). 

I have got to a reasonably stable system; I have the correct driver for the nVidia card on the desktop. I have been able to confirm that the 'xorg.conf' file - (which I copied and renamed from a sample file from the nVidia web-site) -  has the entries which nViida suggests it should. 

I haven't tried installing the nVidia driver with the Ati card installed, on the expectation that this will probably not work.

So the question now is: what is the correct procedure for changing the dispay hardware, - and asscoiated drivers - in a working Ubuntu configuration?

The hardware specs are:

Mobo: Abit KT7A, no raid, latest BIOS from Abit. VIA KT88 chipset; AGP
CPU: AMD Athlon 'Thunderbird' 32 bit processor running at 1.4 GHz, 133MHz system bus. No overclocking -  EVER, as a matter of principle.
Memory: 3 x 256 MB SDRAM
Sound: Creative SB PCI 128
Graphics: Ati  Radeon 7500, 64 MB to be replaced by
              nVidia Riva TNT2 M64  32MB
CD ROM  - BTC Model 24XM reader
LAN: Intel Pro 10/100 PCI card

---

### Post by oldos2er on 2010-02-18
If I were you, I'd keep the ATI card, if possible. Searching through the repositories, it appears there's no longer an Ubuntu-supplied driver for the Nvidia card. You could install the drivers from Nvidia's website, but every time there's a kernel upgrade, you would need to reinstall them.

---

### Post by XEyedBear on 2010-02-19
> **oldos2er said:**
> If I were you, I'd keep the ATI card, if possible. Searching through the repositories, it appears there's no longer an Ubuntu-supplied driver for the Nvidia card. You could install the drivers from Nvidia's website, but every time there's a kernel upgrade, you would need to reinstall them.


Ah! this advice has the very strong aroma of common sense enhanced by a strong base of experience. I would be a fool not to take it. Thanks. This ends my long frustration with getting  a working system.

---

