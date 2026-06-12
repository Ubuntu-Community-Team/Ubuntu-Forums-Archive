---
title: "Ubuntu 15.10 and also 14.04 LTS stuck at installation in dual boot mode with W10"
date: 2015-10-26
forum: Installation &amp; Upgrades
---

### Post by SouheilBs on 2015-10-26
When trying to install ubuntu (both 14.04 or 15.10 also 15.04) in dual boot mode with Windows 10home
on a new MSI GS60 Ghost pro 4k (intel i7 6700HQ ; 16GB RAM, nvidia gtx 970M 3GB)
The installation remain stuck with the following message:
NMI watchdog: BUG: soft lockup- CPU# ...

Does anyone have an idea about this issue and how to solve it

ps: I google it a bit and as a newbie didn't the only thing I understood  is that it might be related to  power issues.
Thanks

---

### Post by oldfred on 2015-10-26
You have an even newer system, so need the newest version of Ubuntu and still may need ppa to get the very latest. Intel releases updates to kernel, support software and video drivers, but it takes a while before in the kernel & then even longer before included in a distribution. So I would only try 15.10.

Somewhat older model, but needed an additional boot parameter.
 MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878)

Are you booting with Intel video or nVidia. And can you set that in UEFI or does it only auto switch?
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset, and perhaps additional boot parameter(s).
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

    
Nomodeset is usually good for nVidia until you get newest nVidia driver installed, but if Intel

 Skylake Intel Core i5 6500: A Great Skylake CPU For $200, Works Well On Linux, 4.3 kernel  for best graphics
[http://www.phoronix.com/scan.php?page=article&item=intel-i5-6500&num=1](http://www.phoronix.com/scan.php?page=article&item=intel-i5-6500&num=1)
Skylake needs this boot parameter:  i915.preliminary_hw_support=1
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support)


      
 Ubuntu Launches Its "Fresh" Proprietary Driver PPA
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)


 New kernels ppa
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)
Ubuntu Kernel Mainline PPA
[http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1)
[https://launchpad.net/~kernel-ppa/+archive/ubuntu/pre-proposed](https://launchpad.net/~kernel-ppa/+archive/ubuntu/pre-proposed)

---

### Post by SouheilBs on 2015-10-30
Thanks oldfred, the nomodeset worked and I managed to go forward and install 15.10

network issue (fixed with the following)===============================================
and then I had to fix the network by following these:

**Killer 1525** specific firmware:
Download:
[https://github.com/kvalo/ath10k-firmware/blob/master/ath10k/QCA6174/hw2.1/board.bin](https://github.com/kvalo/ath10k-firmware/blob/master/ath10k/QCA6174/hw2.1/board.bin)
and put it in the /lib/firmware/ath10k/QCA6174/hw2.1/ folder (create the folder if it doesn’t exist)

 Download:
[https://github.com/kvalo/ath10k-firmware/blob/master/ath10k/QCA6174/hw2.1/firmware-5.bin](https://github.com/kvalo/ath10k-firmware/blob/master/ath10k/QCA6174/hw2.1/firmware-5.bin)
and put it in the /lib/firmware/ath10k/QCA6174/hw2.1/ folder

THEN
cd hw2.1
sudo depmod -a
sudo update-initramfs -u 

modinfo ath10k_pci

sudo service network-manager stop
sudo modprobe -rfv ath10k_pci
sudo modprobe -v ath10k_pci
sudo service network-manager start
=======================================
Then I ve got the wireless network up

**New issue **
once done I made an ndvi driver update through the software update gui

 **NOW**
when I try to boot after choosing ubuntu in the grub menu the first screen come up and ask for the password which I do but it just start doing something and then goes back to the password screen ???

---

### Post by oldfred on 2015-10-30
Sounds like a gui issue which still may be video driver related.
When you boot is not Intel video default.
then you may need this boot parameter: i915.preliminary_hw_support=1
or if nVidia: nomodeset

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by SouheilBs on 2015-11-05
Thanks Oldfred

So these are the latest points:

I can only boot if I set the nomodeset,
 I tried also the nouveau.modeset=0 and it didn't work
 the preliminary support one also didn't work (i915.preliminary_hw_support=1)

The machine is working but still without optimised hardware 
screen at low resolution
and also blutooth is not working 
although I could get the wireless network up

---

### Post by ubfan1 on 2015-11-05
Do you get the login loop (without the nomodeset) when you log into the guest session?  Sometimes leftover config files (hidden files and directories starting with a period) cause problems when switching video drivers.

---

### Post by SouheilBs on 2015-11-06
thanks ubfan1 
no I didn t get the login loop without the nomodeset (without it simply doesn't boot it stuck during the boot)
however I remember at a certain point I had that loop but got rid of it after a new clean install
otherwise where can I check those leftover file you are talking about

---

### Post by ubfan1 on 2015-11-07
The directory command:  ls -a    will show all the "hidden" files starting with a dot.

---

### Post by rashedabdeltawab on 2015-12-14
Has anyone gotten anything else on this? I've tried with 15.10 and 16.04 (only difference is WiFi works out of the box on 16.04 as opposed to needing a linux-firmware package update on 15.10) and I've gotten nowhere at all. It seems that none of the graphics drivers are loading out of the box; i915 just doesn't do anything and the nVidia ones need some configuration to work once you do install them (nouveau is utter crap). With nvidia-352/355/358 and nvidia-prime, after running nvidia-xconfig I can get Xorg to start the driver and correctly connect to the actual GPU, but it can't load the screen/monitor for some reason; it looks like the EDID isn't being read at all. Any help with this would be very appreciated as I need Ubuntu on this laptop before January. Thanks in advanced.

---

### Post by oldfred on 2015-12-14
I think 16.04 now has 4.3 kernel, but will update to 4.4 after it is released and confirmed it works.

 Have Troubles With 4K Displays On Intel Linux? Try The Linux 4.3 Kernel
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4K-4.3-Fix](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4K-4.3-Fix)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2015-11-30-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2015-11-30-wily/)

---

### Post by rashedabdeltawab on 2015-12-15
The kernel version isn't making a difference, 4.2 works exactly like 4.3 with the preliminary hardware flag. For some reason, when I don't use nomodeset, the kernel panics a second or so after displaying the correctly scaled login splash, and when I do use the nomodeset flag, xorg can't read the EDID off my laptop screen. Attached is a log with the nomodeset flag and the nvidia-355 drivers (I played around a bit with xorg.conf to get the nvidia-355 driver to load and I tried adding the monitor settings manually with no avail)

[https://gist.github.com/Rashed97/9c4b7e34ec7b14166806](https://gist.github.com/Rashed97/9c4b7e34ec7b14166806)

---

### Post by oldfred on 2015-12-15
Once you install the nVidia drivers, you should not need nomodeset.
But is system booting with nVidia or Intel. Or is it not a switchable graphics system, just nVidia?

Have not had to mess with xorg since about version 9.04, but had to use nomodeset since for boot until nVidia driver installed. My now older 620GT does just seem to work with 14.04 with nouveau or nVidia.

---

### Post by rashedabdeltawab on 2015-12-15
It doesn't boot with either. I set nomodeset until i install nvidia-355 and nvidia-prime, then if I try to boot normally, it'll crash (black screen, or if it makes it to the login screen it'll freeze on that). It seems like the kernel panics at that point, which I believe is due to the i915 driver misbehaving, but I can't pull logs from it. Using nomodeset, I can't get xorg to detect the screen.

---

### Post by oldfred on 2015-12-15
I thought with Intel nomodeset did not work and you had to use this instead:
Skylake needs this boot parameter:

  i915.preliminary_hw_support=1

---

### Post by rashedabdeltawab on 2015-12-15
Yeah I use that flag (at least when on 15.10, 16.04 doesn't need it since the 4.3 kernel has Skylake support built in)

---

### Post by florian-b on 2015-12-21
> **rashedabdeltawab said:**
> Yeah I use that flag (at least when on 15.10, 16.04 doesn't need it since the 4.3 kernel has Skylake support built in)
Using a 4.3 kernel (Daily build of Ubuntu Gnome 16.04), I have been able to get a similar system (MSI GS60 Ghost Pro Skylake) working pretty well by adding the following kernel parameters : [B]intel_idle.max_cstate=1 nouveau.modeset=0

[/B]There are still some hiccups (overall performance is good but I get some system lags here and there, and the fans seems to be a bit too noisy) but as a temp solution it allows me to use the machine for dev.

---

### Post by xnovoa on 2016-07-04
Hi all,

I have instaled Linux Mint 18 (ubuntu 16.4) in a MSI GP72 6QE using this tuto:
[https://forum.ubuntu-fr.org/viewtopic.php?id=1976971](https://forum.ubuntu-fr.org/viewtopic.php?id=1976971)

Now all work for me

---

