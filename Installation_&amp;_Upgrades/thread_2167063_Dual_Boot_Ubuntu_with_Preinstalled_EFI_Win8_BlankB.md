---
title: "Dual Boot Ubuntu with Preinstalled EFI Win8 Blank/Black Screen"
date: 2013-08-12
forum: Installation &amp; Upgrades
---

### Post by stalemate2 on 2013-08-12
Hello,


I understand this issue is relatively common. However, I have spent the last 4 days reading this forum etc and still cannot install Ubuntu.


I have an HP Envy Desktop (H9-1330eo) with EFI Windows 8 preinstalled on it. Some specs:


CPU: i5-3570K
GPU: GTX-680
1x SSD 16GB
1x HHD 2TB


I am using a USB pen drive with Ubuntu 13.04 64bit (I have also used a Mint and Fedora 19 disc, which generates the same error). There is nothing wrong with the pendrive, as I used it to install Ubuntu alongside win7 on my laptop.


Method:
In Windows 8 I turned off FastStartUp, and used Disk Management to shrink the windows partition as shown in screenshot:


[ATTACH=CONFIG]245305[/ATTACH]




I restart and go into the BIOS and disable Fastboot and Secure Boot. 


I looked into the Intel Smart Response Tech to disable but the only thing I can find is the option to choose RAID, IDE, or AHCI. It was on AHCI, so I left it at that.


Saved BIOS, and restarted, choose to boot from UEFI USB PenDrive. This screen loads:

[ATTACH=CONFIG]245304[/ATTACH]


No matter what option I select here, when I press enter the screen goes blank/black and nothing happens. I have added nomodeset to the end of the linux/boot line and this does 
the same thing. 

I have tried disabling my graphics card in the BIOS and using the motherboards graphics but get the same result.


There is another option to enable Legacy in the BIOS, if I have this turned on and select to boot the UEFI Pendrive, the Ubuntu purple screen starts up. So that works, but 
I believe that is not going to install Ubuntu with UEFI, so I cancelled it.


Any help would be appreciated,
Cheers.

NB: I have looked at these related posts:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[http://askubuntu.com/questions/307508/how-to-tell-if-my-laptop-has-uefi](http://askubuntu.com/questions/307508/how-to-tell-if-my-laptop-has-uefi)
[http://ubuntuforums.org/showthread.php?t=2146179](http://ubuntuforums.org/showthread.php?t=2146179)
[http://askubuntu.com/questions/302118/black-screen-on-installation-of-ubuntu-13-04](http://askubuntu.com/questions/302118/black-screen-on-installation-of-ubuntu-13-04)

---

### Post by oldfred on 2013-08-12
I think only laptops are Ultrabooks that have Intel SRT. But you may still have dual video.
With nVidia you definitely need nomodeset, but new UEFI systems may need other boot parameters also.

The forums link was also a desktop but had Optimus. Do you also have that?

You do not need first two parts of video as you already have Windows. You can review them if you want.
But this is how it is supposed to work. And recent versions of Ubuntu are all the same. Some improvements with each newer version so 13.04 should be better. 
 Intel - Install Ubuntu 12.10 part 3 of series for new system  w/secure boot, part one install keys, part 2 install Windows 8
[https://www.youtube.com/watch?v=_cEwj8bBBC4](https://www.youtube.com/watch?v=_cEwj8bBBC4)

But I think it is the HP's that seem to not install in UEFI mode. Can you boot Windows in UEFI mode on but secure boot off? Windows wiil not boot with CSM/Legacy/BIOS mode.

Video above is with secure boot on, and some systems only boot Windows (or anything) with it on. And then only allow CSM mode with secure boot off. Ubuntu should also install with secure boot on.
I think it has been other HPs that had to install in CSM mode, and then use Boot-Repair to convert from BIOS boot to UEFI boot. You need Boot-Repair anyway to fix grub menu issues.

See also my signature.

---

### Post by stalemate2 on 2013-08-12
Thanks for the reply oldfred.

> **oldfred said:**
> The forums link was also a desktop but had Optimus. Do you also have that?

My bios has the onboard intel graphics disabled, and when I check the Display Adapters on the Device Manage in Win8 it only shows the GTX680. So I believe this is not using Nvidia Optimus.

> **oldfred said:**
> You do not need first two parts of video as you already have Windows. You can review them if you want.
But this is how it is supposed to work. And recent versions of Ubuntu are all the same. Some improvements with each newer version so 13.04 should be better. 
 Intel - Install Ubuntu 12.10 part 3 of series for new system  w/secure boot, part one install keys, part 2 install Windows 8
[https://www.youtube.com/watch?v=_cEwj8bBBC4](https://www.youtube.com/watch?v=_cEwj8bBBC4)

I have watched these videos, in part 3, I get up to 2:05 in the video. I hit install, and only get a black screen. No purple Ubuntu screen.

> **oldfred said:**
> But I think it is the HP's that seem to not install in UEFI mode. Can you boot Windows in UEFI mode on but secure boot off? Windows wiil not boot with CSM/Legacy/BIOS mode.

Yes, I have turned secure boot off and started windows with no problems. I also tried to install Fedora 19 with secure boot on. However, exactly the same problem occurred, I get the black screen after selecting install Fedora on the GRUB menu.


> **oldfred said:**
> Video above is with secure boot on, and some systems only boot Windows (or anything) with it on. And then only allow CSM mode with secure boot off. Ubuntu should also install with secure boot on.
I think it has been other HPs that had to install in CSM mode, and then use Boot-Repair to convert from BIOS boot to UEFI boot. You need Boot-Repair anyway to fix grub menu issues.

See also my signature.

I was thinking that I could install Ubuntu in Legacy mode (as it will install) and then convert to EFI with boot repair as described on [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI). But I am unsure if this works, I have the same concerns as this guy [http://askubuntu.com/questions/216022/dual-booting-ubuntu-12-04-uefi-and-legacy](http://askubuntu.com/questions/216022/dual-booting-ubuntu-12-04-uefi-and-legacy)

Regards

---

### Post by oldfred on 2013-08-12
I think you are booting ok, it just is the nVidia issue. Ever since they added video to kernel about 10.10, I have had the black screen issue on installer and first boot after install or until I install nVidia proprietary drivers. I only realized the issue back then as install flash drive kept flashing like it was still installing but screen turned off.

At grub menu (if UEFI or first boot after install) use e on menu for edit, scroll down to linux line and replace quiet splash with nomodeset. It is a one time change just for this boot. Some of the very new UEFI systems also seem to need additional boot options.

 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
Editing the GRUB 2 Menu During Boot
[https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)

Cannot tell you if you need more settings or not. You will need nomodeset in all cases. Some have posted these:

 UEFI/BIOS
 Some systems need these boot parameters
ACPI=Off nomodeset 
pci=nomsi noapic
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w

---

### Post by stalemate2 on 2013-08-12
I tried multiple variations. At the moment I am trying Linux Mint Cinnamon 15 64bit. I initially selected "Start Linux Mint (compatibility mode)" and it is using the following:

```
linux     /casper/vmlinuz  file=/cdrom/preseed/mint.seed boot=casper xforcevesa iso-scan/filename=${iso_path} ramdisk_size=1048576 root=/dev/ram rw noapic noapci nosplash irqpol\ 1 -- initrd    /casper/initrd.lz
```

Then I changed xforcevesa to nomodeset

Then I used the normal linux install option with nomodeset:

```
set gfxpayload=keep    linux     /casper/vmlinuz  file=/cdrom/preseed/mint.seed boot=casper iso-scan/filename=${iso_path} nomodeset -- initrd    /casper/initrd.lz /casper/initrd.lz
```

as well as your suggestions:
[COLOR=#000000]ACPI=Off nomodeset 
pci=nomsi noapic nomodeset


I have 2 monitors, plugged into each DVI output of my graphics card. Still black screen.


[/COLOR]

---

### Post by oldfred on 2013-08-12
Do not know about Mint. It may need different parameters.

Sometimes the card will output to the wrong port as that depends on default configuration. Are both ports on nVidia card?

---

### Post by stalemate2 on 2013-08-13
Thanks for the replies OldFred.

I went back to using Ubuntu 13.04 64bit, I tried both with a USB pendrive and a DVD.

I used nomodeset with every boot option shown here: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) This is with both monitors plugged into the GTX 680, and onboard graphics disabled. 

Next, I went into the BIOS, and enabled the onboard graphics, disabled the GTX 680, and plugged both monitors into the DVI outputs on the mobo. I tried every boot option as above again.

Still the black screen occurs after selecting "Install Linux".

This is the exact same issue as this guy who also has an HP Envy, and he gave up: [http://ubuntuforums.org/showthread.php?t=2146179](http://ubuntuforums.org/showthread.php?t=2146179)

I think the only solution is to reformat, install win8 in legacy mode, then install Ubuntu in legacy mode.

---

### Post by stalemate2 on 2013-08-13
I have found this post: [http://forums.linuxmint.com/viewtopic.php?f=42&t=121912](http://forums.linuxmint.com/viewtopic.php?f=42&t=121912)

Will give that a try tomorrow: Install linux in legacy mode then convert it to EFI. Sounds dodgy to me, but kinda need linux to run programs for my phd.

---

### Post by stalemate2 on 2013-08-14
Well it worked. Except in Step 7 I had to boot from the Linux Live cd to run boot repair. As it just loaded straight into Windows8.

I checked in Linux if it did successfully use EFI mode by running in terminal:

```
[COLOR=#333333][FONT=monospace][ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" [/FONT][/COLOR]
```

It bounced back: EFI boot on HDD


However, if I go back into BIOS and disable Legacy Mode, then try to run Linux Mint from the GRUB screen it again goes into blank screen. So now I have left Legacy Mode on: and GRUB menu works, with the option to run both EFI Win8 and Linux Mint.

It seems a bit messy, but both OS work.

---

### Post by oldfred on 2013-08-14
Is legacy mode then really either BIOS or UEFI and with legacy mode off it is secure boot?

Some systems  do have auto boot where they check for an efi partition and boot files for UEFI boot, if not found check MBR for BIOS boot, and if not found then give a boot error.

---

### Post by stalemate2 on 2013-08-14
My BIOS has option Legacy: Disable/Enable
If also has Secure Boot: Disable/Enable

For both my Windows and Linux to work I have to have legacy enabled, and seccure boot disabled.

With legacy enabled It seems to mean, as you say, that it looks for UEFI boot firsts, then looks for BIOS boot. 

Cheers.

---

### Post by oldfred on 2013-08-14
Thanks for Update.

---

