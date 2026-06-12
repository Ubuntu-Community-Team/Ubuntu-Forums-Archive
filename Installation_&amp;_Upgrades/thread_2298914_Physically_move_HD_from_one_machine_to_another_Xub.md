---
title: "Physically move HD from one machine to another Xubuntu 15.04"
date: 2015-10-14
forum: Installation &amp; Upgrades
---

### Post by Linzt on 2015-10-14
About two hours ago I had a Lenovo X220 w/Evo 850 SSD containing a CentOS 7 installation on it (yes, a server distro on a laptop - I know, but I'm familiar with RHEL). Several weeks back I'd completed this from scratch through netboot install.

Anyway, I got rid of the installation today due to the machine just freezing up arbitrarily which after several weeks of use my patience with it has worn thin. I did not locate the source of the lock-up problems, but usually found that when copying large files from USB to the SSD or surfing Chrome with >12 tabs open would be sufficient to trigger the problem.

The kernel in use where this problem was present were:

[FONT=courier new]3.10.0-229.7.2.el <-- Would crash on boot part way through
3.10.0-229.el7[/FONT]

Today I tried installing Xubunt from LiveUSB. I thought the problem above was specific to the installation, so was surprised when I found that either the installation GUI would report I/O problems and crash, or just lock up at the 30% way through the "copying files" stage.

To get round the issue I removed the SSD from the X220 into another x86_64 bit laptop (but which has AMD GPU chipset as opposed to Intel in the X220) and installed Xubuntu without trouble so doubt the problem is faulty/dying SSD, but rather the X220 may have some issue electronically (?). In any case, my question after all this is

 * How do I prepare for moving the SSD back into the X220?

I am currently finding that the X220 does not boot. BIOS passes POST, but there is no GRUB menu so I cannot edit the parameters. The screen simply stays black with an intermittent underscore cursor top-left (as I gather it is stuck in a boot-loop).

After putting the SSD back in the other laptop I'm not able to locate the file which configures the GRUB menu so cannot mess with the parameters and regenerate the GRUB config.

So I guess I'm talking hardware here.

 * How do I reconfigure the hardware config for moving back into the X220?

Previously when using CentOS I loaded the kernel module i915 for graphics. Maybe this could be an issue, however there are no proprietary drivers installed on the Xubuntu installation so I would guess the kernel detects the necessary driver and dynamically loads at boot. Could be red-herring then.

Anyway, all suggestions appreciated.

---

### Post by grahammechanical on 2015-10-14
So, when you installed Xubuntu you did not tick the box "Install this third party software" Or, did you? Ticking that box would have installed not only proprietary audio & video codecs but also a proprietary video driver. And the driver would have been suitable for an AMD GPU and not for an Intel GPU. Please check Additional Drivers and confirm that an open source video driver is being used.

The boot loader (Grub) is installed into the master boot record of a hard disk (SSD). So, with the hard disk removed there can be no Grub menu. You should get a message about OS not found & please insert disk with OS. That would be coming from the motherboard's boot system (BIOS/UEFI). You should still be able to enter the BIOS/UEFI boot system configuration utility. 

So, the question from our point of view is this: When you put the SSD back into the X220 do you get a boot menu and can you load Xubuntu? If Xubuntu/Ubuntu is the only OS then we will not get a boot menu. There is no need for one. But we can press Shift as the motherboard goes through its POST to produce the Grub boot menu.

But from what I know about Grub configuration, it is not the place to make adjustments for a different hardware set up. Unless you are thinking about boot parameters such as nomodeset. First, make sure that you are not running Xubuntu with an AMD video driver on an Intel graphic adapter.

Regards.

---

### Post by Linzt on 2015-10-14
Thank you for your reply. 

> [COLOR=#000000]So, when you installed Xubuntu you did not tick the box "Install this third party software" Or, did you?[/COLOR]

I did not.

> [COLOR=#000000]When you put the SSD back into the X220 do you get a boot menu and can you load Xubuntu? If Xubuntu/Ubuntu is the only OS then we will not get a boot menu. There is no need for one. But we can press Shift as the motherboard goes through its POST to produce the Grub boot menu.[/COLOR]

Then there is no Grub menu since Xubuntu is the only OS. I'll try the shift key for nomodeset because...

> [COLOR=#000000]make sure that you are not running Xubuntu with an AMD video driver on an Intel graphic adapter[/COLOR]

I am not running the AMD proprietary video driver. I have also confirmed this from Settings > Additional Drivers.

---

### Post by sudodus on 2015-10-15
Have you checked with memtest if the RAM is good? You need to boot in BIOS mode to run memtest (unless you download a special (free but not FOSS) version for UEFI).

Maybe you can try to run a live system for a longer time, and maybe a persistent live system, to see if the computer will be stable with Xubuntu? You can use [mkusb](https://help.ubuntu.com/community/mkusb) to install a persistent live system with a casper-rw partition (instead of a casper-rw file). Such a live or persistent live system can be installed into the SSD (not only a USB pendrive), and it is definitely portable.

---

### Post by gordintoronto on 2015-10-15
It really sounds like there is a serious hardware problem on the X220, and it's not going to be solved by some software configuration magic. It's probably memory or the motherboard.

---

### Post by Linzt on 2015-10-26
Running Memtest86(plus) v5.01 shows a ton of bad RAM. Currently on test #6 and out of 96% tested only 16% is "good". Pretty clear then. I find this surprising though since I bought the RAM from Amazon brand new when I purchased the X220: Corsair CMSO4GX3M1C13333C, 2x4GB SODIMM's.

---

### Post by sudodus on 2015-10-28
Yes, the RAM seems bad. It is not common, but it happens.

---

