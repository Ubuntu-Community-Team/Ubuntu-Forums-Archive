---
title: "Yet Another Blank Screen During Installation"
date: 2017-01-21
forum: Installation &amp; Upgrades
---

### Post by ctate2 on 2017-01-21
Hi - I'm attempting to install Ubuntu 16.04.1 LTS with no luck.

When I select [FONT=courier new]Try Ubuntu without installing[/FONT], the splash screen loads, the dots animate, the USB lights up; but after a few seconds, the dots stop animating and the USB goes dark. From there, the only thing I can do is CTRL+ALT+DEL to restart.

I've searched for possible causes but haven't found anything that works:

- Adding [FONT=courier new]nomodeset[/FONT] shows me a blank screen instead of the splash screen.
- Adding [FONT=courier new]grub_gfxmode[/FONT] has no effect. I've tried [FONT=courier new]grub_gfxmode=1920x1080x32[/FONT], [FONT=courier new]grub_gfxmode=800x600x32[/FONT] and every resolution in between.
- Turning Hibernate off via [FONT=courier new]powercfg.exe /hibernate off[/FONT] as an admin has no effect.
- There doesn't appear to be a *Fast Startup* option on this notebook.
- Removing [FONT=courier new]silent[/FONT] and/or [FONT=courier new]splash[/FONT] has no effect.
- Adding [FONT=courier new]acpi=off[/FONT] has no effect
- Adding [FONT=courier new]nolapic[/FONT] loads the splash screen which does eventually change...to a blank screen.
- Verifying the ISO/USB image.
- Verified that *Secure Boot* is disabled.

Is there something else I should try? I'm a long-term Ubuntu Server user and want to switch from OS X to Ubuntu Desktop.

I've installed Ubuntu several times in a VM (including on this notebook) with no problem; I'm guessing it has something to do with the video card, but I don't have any external monitors to use for debugging.

Here are my notebook specs:

Sager NP8174
- 7th Gen Intel Core i7-7700HQ Processor
- NVIDIA GeForce GTX 1060 6GB GDDR5
- 32GB (2x16GB) DDR4 2400MHz Dual Channel Memory
- 256GB OCZ RD400 NVMe M.2 SSD
- Intel Wireless-AC 8265 + Bluetooth
- Windows 10 Pro 64-Bit Edition

Any help is greatly appreciated. Thank you very much!

---

### Post by oldfred on 2017-01-21
Usually nomodeset works.
Are you replacing quiet splash to see if other errors then are shown. Often not last entry, but several above where ever it stops.

Are you able to set or limit which video mode is used in UEFI?

Almost all UEFI do have the fast start up as that is one of the advantages. That skips all checks for hardware or configuration changes & just immediately boots. Often no time to even press a key to get into UEFI to change boot order or settings.

New hardware often takes a while before Linux works easily.
Have you tried 16.10 or even 17.04 daily which is not released yet? Newer drivers & kernel may support your very new hardware better.

Once installed you will need Intel driver updates & ppa for newest nVidia driver.
       Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 


 Intel Driver updates
[https://ubuntuforums.org/showthread.php?t=2342137](https://ubuntuforums.org/showthread.php?t=2342137)
Updates often needed for Skylake or Kabylake
[https://01.org/linuxgraphics/intel-linux-graphics-firmwares](https://01.org/linuxgraphics/intel-linux-graphics-firmwares)

---

### Post by ctate2 on 2017-01-21
Thanks - that helped me a lot! I'm now up and running :)

What worked for me is using 16.10 instead, enabling CSM via the UEFI menu which got the Ubuntu installer to run.

After installing Ubuntu, I rebooted, installed the latest Nvidia drivers via System Settings, rebooted, disabled CSM and voila!

Thanks again :D

---

### Post by oldfred on 2017-01-21
You can change to solved.

Did you end up in UEFI mode, but had to have CSM on to install or in CSM boot mode?
Or did you install in CSM/Legacy/BIOS boot mode and use Boot-Repair to convert to UEFI?

---

### Post by annamad42 on 2017-04-19
Similar specs, Intel Kaby Lake and notebook GeForce 1060.

I didn't have CSM in the BIOS (2016 ver.).
What solved the problem was changing the MSHybrid to DISCRETE mode in the BIOS Advanced Chipset Control.
nomodeset helped.

Thought it might save sbdy couple hours of trying.

PS. At the moment, coming back to MSHybrid results in interesting bugs: you can only launch properly your system with an external monitor in mirror mode. Then disconnect and it'll work etc etc

---

