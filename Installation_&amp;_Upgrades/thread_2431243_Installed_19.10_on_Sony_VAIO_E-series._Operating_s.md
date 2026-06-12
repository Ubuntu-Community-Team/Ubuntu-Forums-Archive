---
title: "Installed 19.10 on Sony VAIO E-series. Operating system not found on boot."
date: 2019-11-13
forum: Installation &amp; Upgrades
---

### Post by neko-berry on 2019-11-13
Hi there,

I am pretty new to Ubuntu (used it about 10 years ago) and I am trying to install it on my Sony VAIO E-series laptop.

I created a bootable USB using Rufus and the 19.10 ISO. I was unable to boot it in UEFI mode so I changed my BIOS to Legacy and it booted. I went through the installer and was successful. But now, upon restarting, I get a message saying there is no operating system. I have searched all over the internet to try and figure this out but I am thinking this might be a VAIO specific problem.

I can boot into Windows only when I set the BIOS back to UEFI.

Is this problem to do with installing using the Legacy BIOS? As far as I know, my partitions were all fine. I had a 'biosgrub' partition and also a boot partition where I chose to install the boot files. Then a main partition mounted to /.

My husband who is experienced with Linux can't even figure out where we've gone wrong.

I have disabled fast startup in Windows (I have no idea how that affects things but it was a suggestion I saw).

If anyone has any suggestions for me, please please help. I hate Windows 10 and I am super keen to get Ubuntu running. My laptop is a bit old - probably 5 years - but it's pretty good in terms of specs.

---

### Post by yancek on 2019-11-14
> I had a 'biosgrub' partition and also a boot partition where I chose to  install the boot files. Then a main partition mounted to /.


A 'biosgrub' partition is used by Linux systems to do a 'legacy' install on a GPT partitioned drive.  You can't do that with windows. If you have windows on a GPT disk, you must install it UEFI. From your comments, it appears you have an EFI install of windows (which release??) so you should install Ubuntu UEFI.  Ubuntu has a site which explains all this, see the link below.  If you could not get Ubuntu to boot UEFI, you might try software other than rufus such as etcher although I would expect rufus to work?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Do you get the 'no operating system found' message after you have changed your BIOS firmware to Legacy/CSM boot?  Even if you were able to boot your Ubuntu install, it would be a convoluted process to boot between windows and Ubuntu as you would need to make changes in the BIOS firmware on each boot.  Grub installed in Legacy mode will not boot an EFI install of windows and of course, windows EFI will not boot any Linux AFAIK.

The fast startup, fastboot and anything related to hibernation (this is the default on windows 10) will be a problem as no Linux OS will mount a hibernated partition as there is a high risk or  problems and loss of data so all that should be off. 

So the solution is finding out why Ubuntu would not boot in EFI mode.  Perhaps reading the link above will help or if you are lucky enough to have a manual for the machine with info on the BIOS firmware.  Might do an online search for UEFI firmware on the particular machine.

---

### Post by neko-berry on 2019-11-14
> **yancek said:**
> A 'biosgrub' partition is used by Linux systems to do a 'legacy' install on a GPT partitioned drive.  You can't do that with windows. If you have windows on a GPT disk, you must install it UEFI. From your comments, it appears you have an EFI install of windows (which release??) so you should install Ubuntu UEFI.  Ubuntu has a site which explains all this, see the link below.  If you could not get Ubuntu to boot UEFI, you might try software other than rufus such as etcher although I would expect rufus to work?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Do you get the 'no operating system found' message after you have changed your BIOS firmware to Legacy/CSM boot?  Even if you were able to boot your Ubuntu install, it would be a convoluted process to boot between windows and Ubuntu as you would need to make changes in the BIOS firmware on each boot.  Grub installed in Legacy mode will not boot an EFI install of windows and of course, windows EFI will not boot any Linux AFAIK.

The fast startup, fastboot and anything related to hibernation (this is the default on windows 10) will be a problem as no Linux OS will mount a hibernated partition as there is a high risk or  problems and loss of data so all that should be off. 

So the solution is finding out why Ubuntu would not boot in EFI mode.  Perhaps reading the link above will help or if you are lucky enough to have a manual for the machine with info on the BIOS firmware.  Might do an online search for UEFI firmware on the particular machine.

Hey thank you for your reply.

Yes, I have Windows 10 installed in UEFI, so the ideal was to install Ubuntu the same way but as I said we couldn't get the usb to boot (the laptop went into a boot loop) so we just assumed we could install it in Legacy mode instead. 

I'll try to figure out why we couldn't boot the usb in UEFI. We tried so many things though. We're really stumped.

I'll check out the link you gave. Thanks!

---

### Post by oldfred on 2019-11-14
I have recently seen others using Rufus that could only boot in BIOS mode.
Does Rufus not correctly install Ubuntu?

The Ubuntu ISO is configured for either UEFI or BIOS boot and UEFI systems will normally offer to boot in either boot mode.
But some with Rufus only see BIOS/CSM.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

Windows requires gpt for UEFI on drive, but Ubuntu's flash drive can be MBR or gpt or hybrid DVD/flash and boot in UEFI or BIOS boot mode.
Try selecting gpt as that is more standard with UEFI and see if then Rufus makes a UEFI bootable flash drive.

---

### Post by neko-berry on 2019-11-14
> **oldfred said:**
> I have recently seen others using Rufus that could only boot in BIOS mode.
Does Rufus not correctly install Ubuntu?

The Ubuntu ISO is configured for either UEFI or BIOS boot and UEFI systems will normally offer to boot in either boot mode.
But some with Rufus only see BIOS/CSM.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

Windows requires gpt for UEFI on drive, but Ubuntu's flash drive can be MBR or gpt or hybrid DVD/flash and boot in UEFI or BIOS boot mode.
Try selecting gpt as that is more standard with UEFI and see if then Rufus makes a UEFI bootable flash drive.

I've used a few different applications for making the USB, Rufus first and etcher and there was another... I also tried mounting the iso and dragging the files over to the USB. None worked. 

This afternoon I tried Rufus again and made sure I chose GPT and UEFI when making the bootable USB. Still no luck!! I even managed to find an update to my laptop's BIOS firmware and installed that but there's no change. 

Frustrating problem.

---

### Post by neko-berry on 2019-11-15
Great news! I am typing this from my brand new UEFI Ubuntu install :)

My husband did some research and apparently some systems have buggy BIOS setups. I installed rEFInd to stop Windows being the primary boot manager, and then I was able to boot from my live usb on UEFI and install Ubuntu. Thank you both for your suggestions and help!

---

### Post by yancek on 2019-11-15
> I even managed to find an update to my laptop's BIOS firmware and installed that but there's no change. 

That is often a solution to the problem but I guess not this time.  A number of manufacturers don't comply with UEFI standards so it's hard to know what to do as something which works on one computer won't on another so we end up having to explore the BIOS firmware.  I had difficulty changing the primary boot entry on my HP notebook from Linux but was able to in the BIOS.  I don't use Sony so don't know what they have.  rEfind is excellent software, glad you got it working.

---

### Post by neko-berry on 2019-11-15
> **yancek said:**
> That is often a solution to the problem but I guess not this time.  A number of manufacturers don't comply with UEFI standards so it's hard to know what to do as something which works on one computer won't on another so we end up having to explore the BIOS firmware.  I had difficulty changing the primary boot entry on my HP notebook from Linux but was able to in the BIOS.  I don't use Sony so don't know what they have.  rEfind is excellent software, glad you got it working.

I feel so satisfied after days of trying to get this working that we finally found a solution. And years ago we tried installing elementaryOS on this laptop with no success and I'll bet this was the problem then too. Super satisfaction all around. Thanks again for your input.

With all the stupid problems I've had with this laptop, I won't ever be buying a Sony computer again. (Not surprised they discontinued VAIO.)

---

