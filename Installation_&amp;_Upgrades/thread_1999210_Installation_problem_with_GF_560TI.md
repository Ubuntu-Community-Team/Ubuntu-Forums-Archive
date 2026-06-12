---
title: "Installation problem with GF 560TI"
date: 2012-06-07
forum: Installation &amp; Upgrades
---

### Post by SvEnX on 2012-06-07
I guess this is a common problem, but I don't have time to read all the possible threads.

I'm trying to install 12.04 64bit, but getting weird graphics problems. Looks like a graphics card compatibility problem. I cannot even install Ubuntu as this occurs on the start of the installation.

My system:
Core i5 2500k
Geforce 560TI 1024MB vram.
8GB RAM.


[[img]http://www.upload.ee/thumb/2410443/IMG_20120608_012957.jpg[/img]](http://www.upload.ee/image/2410443/IMG_20120608_012957.jpg)

---

### Post by oldfred on 2012-06-07
If you are installing in BIOS mode not the new UEFI mode.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

---

### Post by bvt on 2012-06-07
I have a GF 550TI and had to remove it from the computer for my USB boot disk to bring up the install screen.  Currenlty running my on-board ATI Raedon 4250, apt-got nvidia's newest driveers from the ppa, and still won't boot to a prompt if I plug power into the 550TI.  

Is there something I can do in GRUB to boot into a low resolution?  BTW when I boot with the 550TI plugged in, the BIOS splash screen comes up.

I have an AMD Athlon(tm) II X4 640 Processor
MSI 880GM-E43 motherboard
8 gig ram

Barry

---

### Post by SvEnX on 2012-06-08
> **oldfred said:**
>  'nomodeset'. 

Thanks, seemed to work for low graphics mode thought when I installed Nvidia's official driver I got the same result as in the first post.

---

### Post by bvt on 2012-06-08
Got mine figured out! had to run nvidia-xconfig, but had to locate it in lib/usr.  That did the trick.

---

### Post by oldfred on 2012-06-09
Is the issue just with grub's menu or after you boot?

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Are you able in BIOS to change which video is being used?

---

### Post by efflandt on 2012-06-09
Just curious if a Gforce 560 Ti or 550 Ti is different from GTX 550 Ti (ie, built-in vs. separate card)?

For 11.10 I had to use **nomodeset** when the nvidia driver was installed (apparently so it would cooperate with nouveau module) or my screen would show "no signal" following grub menu.  But with 10.10 or 12.04 I did not need to use any kernel parameters (all 64-bit). My 12.04 is just on USB hd so far.

---

### Post by Skara Brae on 2012-10-09
> **SvEnX said:**
> I'm trying to install 12.04 64bit, but getting weird graphics problems. Looks like a graphics card compatibility problem. I cannot even install Ubuntu as this occurs on the start of the installation.
Well, I'll be darned, I have the same issue _*just now*_ while trying to install Xubuntu 12.04 on my brand new desktop PC (Core i5-3450, Gigabyte GA-H77-D3S mobo and a Geforce GT 630): black screen with a few weird lines.

Five minutes ago, while trying Xubuntu 12.04 a second time, I got a black screen with a white, blinking cursor. I tried Linux Mint "Maya", and I get a light grey screen with a white, blinking cursor.  WinVista (retail) runs fine (whoa, a"contradictio in terminis"); it was installed by the guy at the computer store I went.

Is this too that !@*%#! UEFI bios nonsense? Hotdammit. I'll (have to) look into it.

*sigh* How I miss my old and loyal Athlon64-based PC (whose specs are still in my signature below)...

Oh, sincere apologies for [*bumping*] this thread.

---

