---
title: "Can't install Ubuntu from DVD"
date: 2015-12-19
forum: Installation &amp; Upgrades
---

### Post by iziren on 2015-12-19
Hello, I'm attempting to do a fresh Ubuntu 15.10 64-bit install on my Lenovo Thinkpad W541. I created an Ubuntu Disk with the .ISO provided. I made sure to run data verification in Nero to verify that the disk is not corrupted. I changed boot order in the UEFI BIOS to boot up from DVD drive first. 

Installation is frozen at the splash screen. It has been this way for 10 minutes. Any other ideas?

---

### Post by oldfred on 2015-12-19
Do you know if when you boot, if you are using Intel or nVidia video?

If nVidia you need nomodeset, but if Intel you may need a different boot parameter added the same way to replace quiet splash in linux line of grub. After install, you will need same boot parameters until proprietary driver installed. Do not install from nVidia but either Ubuntu repository or Ubuntu's new ppa for newest drivers.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132
[/URL]
 # Usually nVidia or AMD work with this:
nomodeset
# Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size

Often UEFI issues are common across models, so even if not your model, these may clarify some of the issues with Lenovo.
 Lenovo rename files
[http://ubuntuforums.org/showthread.php?t=2302170](http://ubuntuforums.org/showthread.php?t=2302170)
Lenovo Laptops there is NOVO button on left side
Lenovo S20-30 BIOS install only
[http://ubuntuforums.org/showthread.php?t=2277003](http://ubuntuforums.org/showthread.php?t=2277003)
T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)
Some Lenovos comes with a physical switch that enables you to select which graphics adapter to use.
 Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124)

---

### Post by iziren on 2015-12-19
Thanks, I'll give that a try, by default, the W541 uses the integrated Intel HD 4600 GPU for less intensive tasks and transitions over to the more power nVidia Quadro K1100M graphics for more graphically intense 3D applications. Thanks for your help! I'll make an attempt of your advice and report back here with my findings/observations.

---

