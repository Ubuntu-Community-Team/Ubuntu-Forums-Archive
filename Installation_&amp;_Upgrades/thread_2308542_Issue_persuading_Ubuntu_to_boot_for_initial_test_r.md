---
title: "Issue persuading Ubuntu to boot for initial test run and install."
date: 2016-01-04
forum: Installation &amp; Upgrades
---

### Post by YosemiteGlory on 2016-01-04
**The Problem:**
I'm attempting to install Ubuntu on my computer from bootable USB, and I'm running into an issue getting it to boot into "try without installing". After hitting that option, it throws up three error messages in this order:

[LIST]
[*]ACPI PCC probe failed. 
[*]radeon 0000:01:00.0: Invalid ROM contents 
[*]usb_submit_urb(ctrl) failed: -1 
[/LIST]
From what I've learned, "ACPI PCC probe failed" means nothing; "radeon 0000:01:00.0: Invalid ROM contents" also means nothing; and "usb_submit_urb(ctrl) failed: -1" seems to have a variety of causes. I feel like I'm missing something.

  **The Hardware:**

[LIST]
[*]Intel Pentium G3258 @ stock clock 
[*]AMD R7 370 (My monitor only has VGA input, so I have an HDMI to VGA adapter hooked up.) 
[*]Gigabyte GA-H81M-DS2V 
[*]Currently running Windows 8.1, no prior Linux installs. 
[/LIST]
**What I've already done (to no effect):**

[LIST]
[*]nomodeset 
[*]Enabled Intel Virtualization Technology in BIOS 
[*]Enabled XHCI & EHCI Handoff in BIOS 
[/LIST]
  I've installed Linux on other computers before, but this is the first time I've encountered issues during the process, so I haven't learned much about troubleshooting or problem-solving. You can safely consider me a noob. Thank you for any help you might be able to give! I appreciate it greatly.

---

### Post by oldfred on 2016-01-04
I might turn off the Intel Visualization. And you should need the nomodeset, but may need other settins also.

 Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS boot) to set ACPI=Off and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

---

### Post by YosemiteGlory on 2016-01-04
Hi, thanks for your reply!

It turns out that my processor actually doesn't support IOMMU (AKA VT-d: [http://ark.intel.com/products/82723/Intel-Pentium-Processor-G3258-3M-Cache-3_20-GHz](http://ark.intel.com/products/82723/Intel-Pentium-Processor-G3258-3M-Cache-3_20-GHz)), so I'm unable to enable that. Disabling IVT didn't have an effect either. Using a USB installer (FAT32) with a smaller than 4GB partition gave the same errors, as did a live DVD. The other threads you linked mostly had to do with bootup time, so I didn't attempt to mess with GRUB. Should I try to do that?

---

### Post by oldfred on 2016-01-04
Have you tried booting with the Intel video, not the AMD card?

---

### Post by YosemiteGlory on 2016-01-04
I switched to the integrated graphics, and in conjunction with the disconnection of a sound card it was able to boot (albeit, the errors still get thrown up first)! Is there a separate procedure for getting the discrete card to cooperate after install?

---

### Post by oldfred on 2016-01-04
I do not know about sound cards and only a little on AMD.
Some links, but as with nVidia you have to install correct version of proprietary driver or you will have issues. And if you do install wrong one, be sure to totally purge first.
Proprietary driver is integrated into kernel so only one can be used and best to install from Ubuntu repository unless you have very new card that versions in repository are not new enough.

       22-Way Comparison Of NVIDIA & AMD Graphics Cards On SteamOS For Steam Linux Gaming Oct 2015
[http://www.phoronix.com/scan.php?page=article&item=steamos-22-gpus&num=1](http://www.phoronix.com/scan.php?page=article&item=steamos-22-gpus&num=1)

I found this in my notes, you may want to check if release notes have been updated.

 With 15.10 Release notes
AMD's fglrx driver does not work with the current kernel
      
 With the upcoming Linux 4.2 kernel will be the premiere of the new "AMDGPU" 
kernel driver to succeed the "Radeon" DRM kernel driver
[URL="http://tech.slashdot.org/story/15/07/25/2014228/amd-starts-rolling-out-new-linux-driver-model-but-many-issues-remain"]http://tech.slashdot.org/story/15/07/25/2014228/amd-starts-rolling-out-new-linux-driver-model-but-many-issues-remain
[/URL]
 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)

the 16.04 is now, alpha release and will be out in April. I do have it installed and it works, but may break on some update. So if not a system you have to totally rely on, you can try it. I typically keep a LTS version as my main working system, but also install each new release just to see what has changed and have another system to boot.

---

### Post by YosemiteGlory on 2016-01-04
This is great info! Thank you for all of your help. I'll mark this as 'solved'.

---

