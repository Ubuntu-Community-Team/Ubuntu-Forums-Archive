---
title: "Problem Installing: No video *only* when installing UEFI vs Legacy BIOS"
date: 2018-12-01
forum: Installation &amp; Upgrades
---

### Post by zaurian on 2018-12-01
I'm not exactly a n00b, but I'm no Ubuntu expert.  I'd like to get Ubuntu installed alongside Windows 10.  I have two 1Tb NVMe drives. First drive is Windows 10 with GPT and UEFI Windows boot.

I booted from a live USB and installed Ubuntu Desktop 18.04 specifically on the second NVMe drive. The install seemed to go fine. However, once I rebooted it went directly to Windows. I realize now that I installed in Legacy BIOS.  I still don't understand why Grub was not installed, however. 

So, on to UEFI BIOS configuration (ASUS ROG Zenith Extreme motherboard, AMD Ryzen Threadripper 16 core, 128Gb RAM). I disabled Legacy/CSM. I also disabled Safe Boot. Then, no option to boot from my USB, because it wasn't set up to boot UEFI.  So, I re-image the USB this time using Rufus 3.3 and a GPT partition scheme with UEFI, imaging as ISO not DD.  Reboot and now I see the USB as an option so I make it the first boot choice. EFI menu comes up: live, live-install, check, memtest, hd (full descriptions as seen in txt.cfg in isolinux). Whether I choose live or live-install, I get a black screen for a few seconds and then there is no HDMI signal to my monitor.

I know that the installation has the correct drivers for my HDMI monitor (LG 65" OLED65C7P) and video card (nVidia GeForce 1080Ti) because it worked just fine when I went through the install following a Legacy BIOS boot and install.

I know that the installation program is continuing to run because after about a minute of no signal to my monitor the workstation gets DHCP and I'm able to ping it.

I have exactly the same problem when trying to boot **any** UEFI USB image.  I've tried imaging the Ubuntu install ISO with multiple programs. I've also tried imaging the Boot-Repair ISO, which also works if I do it Legacy but does the same black screen to no HDMI signal following the EFI selection menu popping up. 

I've tried a preseed to enable SSH, but I'm still unable to SSH to it and I'm not 100% sure I'm doing the preseed file properly anyway.  But it sure seems like there must be another way since I was able to see the installation screens when booting Legacy instead of UEFI. 

[LEFT][COLOR=#222222][FONT=Verdana]Also, just as a side note, I have been unable to boot back in to the Legacy BIOS Ubuntu install since the original installation. When CSM is enabled for Legacy boot I get the option to boot the second NVMe drive but it doesn't actually boot. When CSM is disabled (in UEFI only mode) then I obviously don't have that drive or its partitions available as an option.

I've been pulling my hair out on this for hours now. Anyone have any thoughts on things I can try?

Thanks
Steve

EDIT: I have tried the same UEFI Ubuntu install USB on another machine and it works fine. The difference, however, is that the other machine has an integrated video card, which is where the display was output. I took the GTX1070 out of that second machine and tried it in the problem machine. The Asus ROG Zenith Extreme X399 motherboard does not have integrated graphics. I tried multiple different PCI slots. I can boot in to Windows fine with the 1070, but again the UEFI boot to Ubuntu leaves me with no video regardless of PCI slot or either the 1070 or 1080Ti video cards.
[/FONT][/COLOR][/LEFT]

---

### Post by zaurian on 2018-12-02
Solved. I finally was able to get the install working; for some reason, the default drivers appeared to activate *whichever HDMI port was **not** plugged in.* Also, my 16x PCIe slot did not work at all with these drivers.  By moving my video card to PCIe slot 3 (8x) and then moving the HDMI connection **after** the USB booted UEFI up to the install screen, I was able to install Ubuntu and subsequently install the nVidia drivers.  After installing the nVidia drivers I have had no more problems with mysteriously switching HDMI ports and the 16x slot now works fine.

---

