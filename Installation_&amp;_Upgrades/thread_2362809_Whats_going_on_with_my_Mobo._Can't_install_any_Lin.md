---
title: "Whats going on with my Mobo. Can't install any Linux"
date: 2017-06-02
forum: Installation &amp; Upgrades
---

### Post by Langney on 2017-06-02
I used to be able to boot into any flavor of Linux. No it seems i get to the Ubuntu Splash screen and a second or two later it goes black and my monitor says no signal. I have all the same settings on my pc as i used to. Just now it seems whatever i do i can't even get to the area. I tried to install elementaryOS. But about halfway though I'm greeted by an error screen saying bad disk or hard drive or something. I've tried on both my normal HD and my SSD. I just need some tips going forward really as it's driving me up the wall. Weird thing is I can install any Windows OS. I've checked Secure boot too. Any help or tips would be amazing. Thanks


My Specs are 
 
> ystem Manufacturer: RM plc       System Model: RM DESKTOP ECOQUIET 214
               BIOS: BIOS Date: 02/22/13 08:59:42 Ver: 14.01
          Processor: Intel(R) Core(TM) i5-3470 CPU @ 3.20GHz (4 CPUs), ~3.2GHz
             Memory: 8192MB RAM
Available OS Memory: 8148MB RAM

 Card name: NVIDIA GeForce GTX 970
       Manufacturer: NVIDIA
          Chip type: GeForce GTX 970

---

### Post by yancek on 2017-06-02
If you are getting a black screen, you could try a one time edit of the boot menu.  When you see the boot menu from the install media, hit the 'e' key and use the keyboard arrows to scroll down to the line beginning with 'linux' and add 'nomodeset' to the parameters at the end of the line and continue booting.

So what's on the disk now, some version of windows (which one)?, UEFI or MBR install?

If you are getting an error during the install, it would be helpful to note and post the specific error.  If you have windows 8 oir 10 with UEFI, the Ubuntu documentation below should be helpful.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Langney on 2017-06-02
Hi Yancek. At the moment i have Windows 7 on my pc. It's not UEFI. It must be MBR.

---

### Post by oldfred on 2017-06-02
You have newer UEFI hardware, but Windows 7 installer from DVD is BIOS only. If you want UEFI you can copy Windows to flash drive and move & rename some files to make it UEFI bootable.
How you boot install media UEFI or BIOS for both Windows & Ubuntu is then how it installs.
Windows in BIOS boot mode only can use MBR partitioning.
Windows in UEFI mode can only use gpt partitioning.

So if now MBR and you want to keep Windows you need to boot Ubuntu installer in BIOS/MBR boot mode.

You have nVidia card.
Did you install nVidia drivers? Or permanently set nomodeset?
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by Langney on 2017-06-02
Thanks Oldfred. I've gone through everything and its still not letting me get past a black screen, Even after i did what was suggested. I cannot even get to a grub menu :(

---

### Post by oldfred on 2017-06-02
If grub is installed:
If BIOS boot mode holding shift key should bring up grub menu.
If UEFI boot mode pressing escape key (perhaps more than once) should bring up grub menu.

But if you have UEFI fast boot on, then you may not have time to press any keys and it just goes to immediately booting.
Fast boot is to speed booting by eliminating UEFI checking hardware. It assumes no change and previous check of hardware or configuration has not changed.
Often cannot even get back into UEFI to change setting as assumes you get to it from Windows reboot or grub last menu item.
Cold boot often then works, not warm reboot.

---

### Post by Langney on 2017-06-02
Would taking out the Motherboard battery help? Also i have taken a video which i will upload in a few moments which might help

---

### Post by oldfred on 2017-06-02
The last resort of resetting UEFI is removing battery or jumping pins on motherboard. Normally cold boot should work.
You have to fully power down. Remove power, remove laptop battery if laptop. And hold power switch for 10 sec or so to drain any remaining power. The reboot and immediately press correct key to get into UEFI. Best then to turn off fast boot in UEFI at least until fully reconfigured.

Removing battery on motherboard. 
That resets everything back to UEFI defaults. With my motherboards I have had to make many setting changes in UEFI. But that varies by brand/model of motherboard. Also updating UEFI resets.

Newer UEFI motherboards let me take screenshots and save. And one gave a list of changes I had made, before settings save in UEFI.
Older BIOS I had to use camera to take screen shots to know all my settings.

---

### Post by KillerKelvUK on 2017-06-07
Hey, I'm currently having the same issue albeit I'm passing my GTX 970 through to a kvm/qemu virtual machine so not 100% aligned but given the plethora of blank screen issues reported for the 970's we may have some overlap. Would be good if you could comment back and confirm which ubuntu version(s) you've attempted to see if you get the same results in the non-virtual world?

For reference my host is an ASRock Z97 with an Intel i7-4790S, my host desktop comes off the CPU's HDMI out and I use the GTX 970 for kvm/qemu guests only, I use Ubuntu 17.04 on the host. For clarity I've been running GTX pass through with VFIO to a Windows guest now for years successfully, however my very recent attempt to do this with an Ubuntu guest is where I've hit all the display issues.

So my testing so far, ubuntu-server variants only i.e. no GUI of any shape/size...

[TABLE="class: outer_border, width: 500"]
[TR]
[TD][/TD]
[TD="align: center"]**Nouveau**[/TD]
[TD="align: center"]**Nvidia (v375.66 run file)**[/TD]
[/TR]
[TR]
[TD]Ubuntu 17.04[/TD]
[TD]Grub shows but then display corruption, OS is functional tho i.e. SSH works. Grub edits for nomodeset have no effect.[/TD]
[TD]As per Nouveau but also with nvidia-smi displaying accurate results. Grub edits for nomodeset have no effect.[/TD]
[/TR]
[TR]
[TD]Ubuntu 16.04[/TD]
[TD]Grub shows, I then get boot output and then get a login prompt. Perfect![/TD]
[TD]Grub shows, then nothing...blank screen.  SSH still works tho so OS is functional. Grub edits for nomodeset have no effect.[/TD]
[/TR]
[TR]
[TD]Arch Linux[/TD]
[TD]Grub shows then blank screen.  However grub edit with nomodeset resolves the issue and I get a login prompt[/TD]
[TD]Not attempted yet.[/TD]
[/TR]
[/TABLE]

The same virtual machine config runs Windows 10 fine and whilst I can't rule out the virtual aspect being a contributor to my own issues my thoughts are that this is about the card and ubuntu's more recent kernels given the many other reports online for similar issues.  Be great if you can confirm if you've tested with 16.04.2?

---

