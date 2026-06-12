---
title: "Trying to install Ubuntu on an Acer one 10 (S1002)"
date: 2015-12-04
forum: Installation &amp; Upgrades
---

### Post by hsun749 on 2015-12-04
[COLOR=#333333]Hey there guys,
[/COLOR][COLOR=#333333]I have been out of the linux loop for a while so please bare with me.[/COLOR]
[COLOR=#333333]I'm trying to install Ubuntu on my Acer one 10. [/COLOR]
[COLOR=#333333]It's a tablet/laptop hybrid, and it has nothing but a micro usb slot, a [/COLOR][COLOR=#333333]micro sd card[/COLOR][COLOR=#333333] slot, and a regular usb 2.0 slot on the attachable keyboard.
 I don't think the computer picks up the USB 2.0 slot (doesn't display as a bootable option in the bios when i plugged in a flash drive). So, I am currently trying to boot off a micro [/COLOR][usb flash drive]("http://skimlinks.pgpartner.com/mrdr.php?url=http%3A%2F%2Fskimlinks.pgpartner.com%2Fsearch.php%2Fform_keyword%3Dusb%2Bflash%2Bdrive")[COLOR=#333333] (was originally trying Gentoo, now trying Ubuntu). I have prepared a drive with the latest ubuntu ISO using UNetbootin. 
[/COLOR]
[COLOR=#333333]Unfortunately, I have been unsuccessful in booting off the flash drive. [/COLOR][COLOR=#333333]I see the option in the boot up menu, and it reads UEFI: [/COLOR][Sandisk]("http://www.amazon.com/SanDisk-Electronics/b/ref=amb_link_1432992_29?ie=UTF8&node=1092212&pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-4&pf_rd_r=18FYFJ4WWT23SGF6BF22&pf_rd_t=101&pf_rd_p=1261242042&pf_rd_i=226721")[COLOR=#333333], but when I attempt to select this option, nothing happens, the screen goes black for a minute, and then appears to restart, going back to the boot splash image and boots into windows. [/COLOR]

[COLOR=#333333]People have suggested disabling UEFI in the bios but I can't seem to do this. I also tried disabling secure boot but that hasn't worked for me at all. All in all my bios tweaking options seem very limited. I'm not sure what to do next, I'm usually able to figure out a lot of problems like these on my own through google and going through the forums, but it doesn't appear that very many people have this particular computer. 

[/COLOR]I'm not sure if it is something funky with the micro usb drive or if it's something with UEFI, it's the first time I've tried booting off of these. 



[COLOR=#333333]Any ideas? Help would be greatly appreciated![/COLOR]

[COLOR=#333333]Thanks guys![/COLOR]

---

### Post by bjc2 on 2015-12-04
Windows 10 has taken over these devices if you turn on bitlocker, so make sure it's been disabled. According to this post [http://ubuntuforums.org/showthread.php?t=2282184&p=13339143#post13339143](http://ubuntuforums.org/showthread.php?t=2282184&p=13339143#post13339143) , use rufus to make the drive from your iso, then add the bootia32.efi to the EFI/BOOT directory from this [http://askubuntu.com/questions/392719/32-bit-uefi-boot-support](http://askubuntu.com/questions/392719/32-bit-uefi-boot-support) , disable secure boot and put usb devices ahead of the hardrive in the bios , and it should boot your linux.  You have a better laptop than they are using, so your usb 2 plug in your base should work fine. Let us know how it works.

---

### Post by bjc2 on 2015-12-06
I can't get it to install, so will have to wait for this bug [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1341944](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1341944) to be fixed.

---

### Post by megawatt2 on 2015-12-06
Buy an external CD/DVD drive and plug that in

---

### Post by Bucky Ball on 2015-12-06
Welcome. Check whether Windows is installed in UEFI. If it is, Ubuntu should be. If Windows is UEFI, you need to boot to Windows, switch off hibernate (and faststart I think it's called). You should then switch off secureboot in the BIOS and make sure you are set to install Ubuntu in UEFI.

If Windows is not installed with UEFI mode, then booting the USB in UEFI and attempting to install Ubuntu UEFI is not the way. Bottom line: install in same mode as Windows.

You may be doing everything just fine but your machine is just not handling a full, modern Ubuntu. What are the specs of the machine, particularly the amount of RAM? By the sounds of it, that is a fairly low-spec beast and you may be better with Lubuntu or Xubuntu. Try one.

* Just had a look. You have 2Gb in there? Should work, but with that processor I'd still be going for Lubuntu or Xubuntu (Xubuntu is my personal preference). You will enjoy a better and faster computing experience.

> **megawatt2 said:**
> Buy an external CD/DVD drive and plug that in

Unnecessary and unrelated. What difference would that make? Then you have a redundant new drive and no way of installing Ubuntu. Still got to install Ubuntu somehow which is what this thread is about. :-k

---

### Post by bjc2 on 2015-12-07
1.ubuntu15.10-64bit won't boot
2. ubuntu15.10-64bitW/bootia32.efi boots to grub but black screen on any selection even with quiet splash deleted have to use power button to stop
3.ubuntu15.10-32bit won't boot
4. fedora23-64bitW/bootia32.efi won't boot
5. 20150810fedlet-64bit boots but keyboard doesn't work, screen is rotated left, touchpad is disoriented, touchscreen does not work, alt-reisub fails
6.ubuntugnome15.10-64bitW/bootia32.efi boots to grub but black screen on any selection have to use power button to stop
7. linuxmint17.2cin64bitW/bootia32.efi boots to grub but black screen on any selection have to use power button to stop
8. ubuntuNETmini15.10-64bitW/bootia32.efi boots to grub but black screen on any selection even with quiet splash deleted have to use power button
9. lubuntu-64bitW/bootia32.efi boots to grub but black screen on any selection have to use power button to stop
10. xdaT100MagicStick boots to ubuntu 15.04 but keyboard not working, touchscreen not working, touchpad works for left click only and right click by two finger tap, no network wifi, no bluetooth, can mount/unmount usb, an old usb keyboard works, a usb mouse works, the battery doesn't show up, all this runs off the battery only, installed to microssd with grub to main ssd, screen blacks out normally, reboot went into windows, m-ssd was written on, grub appears in bios boot menu, have to change order to put grub before windows to get it to show up, booting into grub gives grub-rescue error: no such device: 93515e25-3020-41ce-b863-a18f79983309. entering rescue mode, seems like 32 bit grub, I guess when secure boot is disabled, ubuntu installs the old 32bit grub which won't boot.
11. ubuntu14.04.3-64bitW/bootia32.efi boots to grub but black screen on any selection even with quiet splash deleted have to use power button to stop

I wonder what causes the black screens on the installer. I can't find any way to troubleshoot. And why does the magic stick work? Maybe my hardware is bad. Can someone who owns this confirm the same problems?

---

### Post by Bucky Ball on 2015-12-07
Have you tried using the nomodeset option? Not sure when you're deleting quiet splash (which shouldn't make a lot of difference), whether that is once you've installed or before.

I suggest you boot to something that is going to take you to the initial install screen with the 'Try Ubuntu' 'Install Ubuntu' etc. options (I presume one of the methods gets you've outlined above gets you there (sorry, didn't read through details as a paragraphless block of text is too much for my aging eyes)), and as things are booting you get to a screen with a purple screen and an icon down the bottom. Hit any key then.

This will take you to a regular 'Try Ubuntu' 'Install Ubuntu' screen with a difference. Hit F6 and a pop-up of options will appear. Choose 'nomodeset' and proceed to 'Try Ubuntu'. Any luck?

---

### Post by bjc2 on 2015-12-07
I tried nomodset and no.  So I exchanged it rather than wast more time.

---

### Post by hsun749 on 2015-12-07
So simply by copying the bootia32.efi file mentioned in the post that you linked to the /efi/boot directory and disabling secure boot has allowed me to successfully boot onto the live media. My guess now is to take the approach here to install linux on a "32 bit UEFI" system:

[http://askubuntu.com/questions/392719/32-bit-uefi-boot-support](http://askubuntu.com/questions/392719/32-bit-uefi-boot-support)

---

### Post by hsun749 on 2015-12-07
I was actually concerned about whether the machine could handle Ubuntu or not. I'm definitely looking into those distros that you mentioned now that i am able to boot onto the flash drive. Thanks for the suggestions!

---

### Post by bjc2 on 2015-12-08
I no longer have thsi so can't test it anymore. Now I have an asus t100-taf.

---

