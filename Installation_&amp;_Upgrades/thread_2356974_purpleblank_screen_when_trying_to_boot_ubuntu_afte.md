---
title: "purple/blank screen when trying to boot ubuntu after first installation."
date: 2017-03-28
forum: Installation &amp; Upgrades
---

### Post by fleskil on 2017-03-28
hello. 

can somebody please help me. ive been trying to make this work for 2 days. i used a usb stick to install ubuntu. booting live from usb is working. but the installation to ssd has been hell. i have tried so many things. im trying to dual boot with windows.
i have ran into so many problems. finally i was able to get the grub boot menu when booting. i was really happy when that happened. the problem was that it was booting in secure mode.
the joy did not last for long.   now i just get a blank/purple screen after trying to run Ubuntu.

i have tried everything. i have googled so much, but nothing seems to work. everytime i solve one problem then theres another one.
have tried asking on ubuntu irc.

someone please help.

---

### Post by oldfred on 2017-03-28
What video card/chip?
What brand/model System.

Often video issues can be solved with boot parameters until you install proprietary drivers from Ubuntu's repository. Some systems require other boot parameters instead or in addition to nomodeset.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by RobGoss on 2017-03-28
What distribution are you trying to install, try to give as much information as you can about your system

---

### Post by fleskil on 2017-03-28
Thanks for the reply.

I have tried nomodeset many times in many different ways by following many different guides. Nothing happens.
I have installed/uninstalled many times. On the last install i chose to overwrite the current install. Prior to this i installed using the "something else" option. Also here ive followed guides.

Its an Acer Switft SF314-51 Signature Edition with Intel(R) HD graphics.

Edit: Trying to run Ubuntu 16.04.2 LTS

RobGoss: Not sure what info thats relevant. Do you need more info? Ill find it if so

---

### Post by yancek on 2017-03-28
You indicate you are trying to dual-boot with windows but do not specify which version of windows you are using which could be very significant.  If you are using 8 or 10 and it was pre-installed, it was most likely an EFI install which Ubuntu would have to be also.  Take a look at the Ubuntu documentation at the link below and compare the instructions to what you did.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2017-03-28
Are you installing in UEFI boot mode?
Are you dual booting with Windows?

Have you updated UEFI/BIOS from Acer?

Issues are often common across brand and even models, particularly if same cpu Intel or AMD.

All Acer we have seen have a unique requirement of enabling an UEFI password & setting "trust" from within UEFI of the /EFI/ubuntu .efi boot files.
       Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[URL="http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392"]http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392

      [/URL]
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 
    [URL="http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392"]
[/URL]

---

### Post by fleskil on 2017-04-01
Well now windows doesnt want to boot.

more info: Windows 10, preinstall. Yes its EFI.
Dual boot with windows.
Installing in UEFI boot mode.

I decided to write a detailed log of what ive done so far:


Log:


disable srt(did not check with driverview)


Tried this: 
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
Managed to screw up the naming.
Sets bios and secure boot to setup defualts.
Renames them properly.
IGNORES fwupx64.efi (since its not mentioned in post)
Sets grub, shim and mokmanager first on boot priority order.
Secure boot enabled.
Tries to start ubuntu.
Goes into grubmode as usual. Purple screen when i try to boot.
Decides to put fwupx64.efi in there.
Secure boot still enabled.
Tries to boot Ubuntu.
Same thing happens.
Disables secure boot.
Tries to boot Ubuntu.
Still purple screen.
Enables secure boot( i red that i should be on)
Puts shimx64.efi on top of boot priority order.
Tries to boot, same problem.
Tries nomodeset. Doesnt work.
Tries to boot windows from grub. Gets bluescreen with error: INACCESABLE BOOT DEVICE
Puts fwup on bottom of priority(i dont know why, im just trying everything)
Puts also grub, shim and mokmanager on bottom.
Tries to boot windows.
Bluescreen with error message InACCESABLE BOOT DEVICE.
Restores Secure boot to factory settings(because i need windows)
On boot says secure boot failed.
And message that says windows boot manager has been blocked by the current security policy.
Disables secure boot. Same problem. 0xc0000225 is the error code.
Sits in shower and cries.
Updates thread on Ubuntu forums.

Please help.

Edit: This is what ive tried after i made the thread.

---

### Post by oldfred on 2017-04-01
Often better to have UEFI Secure boot off.
You should not need mokmanager as that is for managing Secure Boot keys. Ubuntu uses the Microsoft key and unless creating your own kernel & key you should not need it.
You may need  fwupx64.efi as that is directly into UEFI from grub menu. 
If you have fast boot (Which is different from Windows fast start up which also should be off) on then you may not have time to press a key to get into UEFI or one time boot menu key.
Did you upgrade UEFI from Acer?

Do not know Windows error codes, you may have to separately look that up. 
Windows should always boot Windows from UEFI boot menu. 
But grub only boots working Windows so it fast start up turned on or it needs chkdsk you need to directly boot and see it f8 works or use a separate USB flash drive with Windows repair console.
You should be able to boot using shimx64.efi whether secure boot is on or off. Then you may not even need the grubx64.efi. But grubx645.efi will not work with Secure boot on. And you have to have signed kernel installed for Secure boot to work.

I have a Gigabyte Motherboard and the Skylake just boots. But there is an Intel driver update that you should install once it is working. Not sure if I had to use nomodeset originally or not.

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by fleskil on 2017-04-03
Thanks again for helping.

No i did not get to update BIOS. Windows refused to boot before i got the chance to try that. Its not possible to update trough ubuntu?

I tried to run windows repair, but it did not work. After trying for hours i gave up.. I thought well then ill just install ubuntu on the whole partition. No dual boot..

buuut, linux is now kind of working. i had the same problems when i installed only linux, until i tried a boot parameter that i had not yet tried. It was acpi=off...

Now i can log in atleast. But i can not use the touchpad or dim the lights.. I have tried the other parameters(f.ex acpi_osi = "Linux" and just acpi_osi=)
But that does not seem to work.

Ive red that if this happens the ACPI is not compitable with Ubuntu.

What would be next step?
Do you still need the bootInfo summary report?

---

### Post by oldfred on 2017-04-03
You update UEFI/BIOS from UEFI, not normally from an operating system.
My desktop motherboard has three ways to update. A separately bootable flash drive. A file on the flash drive. And direct from within UEFI.
Most use a file and read that some where ever you may have saved it. Often has to be FAT32.

You should be able to directly boot Windows from UEFI one time boot key, often f10 or f12.
But if it needs repairs then you can try f8 for its internal repair console or use your Windows repair disk or installer repair console.

What generation Intel Chip. My Skylake has an update available. And it is combined with the Kabylake update, so now it gives a warning that the Kabylake driver may be needed, (Not).

 Intel Driver updates
[https://ubuntuforums.org/showthread.php?t=2342137&p=13565767#post13565767](https://ubuntuforums.org/showthread.php?t=2342137&p=13565767#post13565767)
Updates often needed for Skylake or Kabylake
[https://01.org/linuxgraphics/intel-linux-graphics-firmwares](https://01.org/linuxgraphics/intel-linux-graphics-firmwares)

---

### Post by fleskil on 2017-04-03
No you see, there is no more Windows. I deleted it. SSD now only contains Ubuntu. I was not able to repair it and i was not able to boot trough f12 I am not trying to dual boot anymore.


I red on the Acer forums that it is not possible to update bios trough another OS than Windows..(?)
Its not possible to update within UEFI. It seems like i have to use freeDos to update bios?

[https://www.acer.com/ac/en/US/content/support-product/6938?b=1](https://www.acer.com/ac/en/US/content/support-product/6938?b=1) <---- link to acer bios update

My version of UEFI/BIOS is 1.07

I have also been reading here:
[https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

[COLOR=#333333][FONT=&quot]" If "acpi=off" allows the system to boot, try to isolate the ACPI issue with the following boot parameters[/FONT][/COLOR][COLOR=#333333][FONT=&quot]Try booting with "acpi=ht"This disables all of ACPI except just enough to enable Hyper Threading. 

If acpi=off works and acpi=ht fails, then the issue is in the ACPI table parsing code itself, or perhaps the SMP code.

The thing is that acpi=off works and acpi=ht fails...      I have no idea if this is relevant.

I understand that i should first update UEFI/BIOS but it seems like a hard thing to do on Acer without Windows....?? 

I am reaally struggling here. [/FONT][/COLOR]

---

### Post by fleskil on 2017-04-03
Maybe its better to just install in legacy or something?

---

### Post by oldfred on 2017-04-03
FreeDos is just a flash drive with the very old DOS type bootable system, like Microsoft before Windows.
Often instructions on updating BIOS include details and perhaps the files to make a FAT32 DOS bootable flash drive.

Your manual in link to updates to "BIOS" does not mention how to do updates. Is there another manual or just all inside UEFI/BIOS?
Or if you download update, does that include the instruction file?

Have you tried to set a supervisory password and enable trust on the grubx64.efi and shimx64.efi from UEFI? See post #6 above for other Acer users who did that and then system worked.

---

