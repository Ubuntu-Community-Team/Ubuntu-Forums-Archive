---
title: "Dual boot: black screen after apparently successful Ubuntu 15.04 installation"
date: 2015-09-13
forum: Installation &amp; Upgrades
---

### Post by hans12345 on 2015-09-13
When I try to install Ubuntu 15.04 as a UEFI dual boot with Win 10, I get stuck in an installation loop.

The All in one PC is a Lenovo C260. I have recently installed a similar dual boot on an ACER desktop and after some problems (thanks OldFred), got that to work.

Initially I had a problem with the USB drive with Ubuntu on it was not seen by the PC but when I used Rufus to create the Ubuntu USB drive, the installation was able to start.

I followed the path outlined on the page "Dual Boot Windows 8.1 And Ubuntu" [http://linux.about.com/od/LinuxNewbieDesktopGuide/ss/The-Ultimate-Windows-81-And-Ubuntu-Dual-Boot-Guide.htm]("http://linux.about.com/od/LinuxNewbieDesktopGuide/ss/The-Ultimate-Windows-81-And-Ubuntu-Dual-Boot-Guide.htm")

Fastboot is off. Secureboot is on.

I go through the installation of Ubuntu quite normally. It appears to be properly installed.

It requests a restart. Then the problem happens, it does not close down, and I am left with a black screen. No BIOS, nothing. I cannot switch to a command shell.

I am forced to power off with the power switch. 

When I power on again, GRUB comes up and only offers me the standard installation options. There is no Ubuntu at the top of the menu. I can repeat the installation process, and this time it asks if I want to replace the existing Ubuntu installation. Having no useful alternative, I say yes. Ubuntu again appears to be correctly installed. But it again gives a black screen and freezes when I try to restart.

I would appreciate any good ideas and advice.

---

### Post by yancek on 2015-09-13
> When I power on again, GRUB comes up and only offers me the standard installation options. 

An installed Ubuntu system will not give you any installation options.  The installer will not be on an installed system.  Are you removing the flash drive you used for the install and changing the boot order in the BIOS?  Is your windows installed using UEFI and if so, did you install Ubuntu using UEFI?

---

### Post by hans12345 on 2015-09-14
> **yancek said:**
> An installed Ubuntu system will not give you any installation options.  The installer will not be on an installed system.  Are you removing the flash drive you used for the install and changing the boot order in the BIOS?  Is your windows installed using UEFI and if so, did you install Ubuntu using UEFI?

You are 100% correct Yancek ! A silly mistake.

All I can say is that it was late at night and since the running Ubuntu crashed (black screen etc) just after asking me to restart, it did not warn me to take out the USB drive with Ubuntu on it.

Nevertheless, my problem remains. When I take out the USB drive and boot up, I go straight back to Win 10, no GRUB etc.

Why does Ubuntu crash on closing down?

---

### Post by oldfred on 2015-09-15
Do not think we have seen your model Lenovo. And every brand/model seems to be a bit different.

What video chip is your Lenovo using?

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

### Post by hans12345 on 2015-09-16
Thanks OldFred

The C260 is an All In One PC (my wife does not like the big system box of my desktops) and has the basic Intel HD graphics. Celeron J1800 CPUs. Win 10 installed. Trying to dual boot Ubuntu 64-bit 15.04

I cannot find a Lenovo NOVO link anywhere.

UEFI BIOS notes:
I have the Supervisor Password Installed, I did this on the ACER that I worked on last time, and it seemed a good idea here too.
Secure Boot: Enabled
Quickboot : disabled
Under security, I see an entry 'Lenovo Service Engine' This is enabled.
Under Startup, I can move the devices up and down (e.g. I have USB at the top, the CDROM etc), except that the entries for 
  HDD: Windows Boot Manager
  HDD: Ubuntu
both move together as one. I cannot put Ubuntu above  Windows Boot Manager

I have looked at all the links in your post. I cannot see a way forward for the C260.

My main worry is that Ubuntu seems to be installed (it works) but crashes on shutdown and of course then is unable to complete the full installation.

Would a list of partitions help?
Are there Ubuntu log files which I could find that are useful?
Shall I try with Secure boot off?

---

### Post by oldfred on 2015-09-16
If you turn secure boot off, can you still boot in UEFI mode. You should, but some make it difficult or default to CSM/BIOS/Legacy.
With Ubuntu you can upgrade to signed kernels and use shim (signed grub version) for secure boot after installing if desired.

HP, Sony & others have modified UEFI to only boot by description and only description that work is "Windows". So for dual booting we modify /EFI/Boot/bootx64.efi to really be grub or shim. All external drives boot using bootx64.efi as a drive boot. But you can use that for internal drives as well. 

If install is failing, where is it stopping? Sometimes grub refuses to install as something particular in configuration is not correct. Or if RAID setting is configured in UEFI/BIOS, even if not used.

Post this from terminal in live installer, but do not expect to see anything:
sudo parted -l

What video card/chip. If very new Intel it may need a boot parameter.
       Lenovo Yoga 11s (Intel i5/Intel HD 4000)
Needed this: acpi_backlight=vendor 
[http://ubuntuforums.org/showthread.php?t=2188199](http://ubuntuforums.org/showthread.php?t=2188199)
[URL="http://ubuntuforums.org/showthread.php?t=1911972"]http://ubuntuforums.org/showthread.php?t=1911972
[/URL]
 screen brightness was 0 during installation, use f12
Lenovo Z580 laptop
[URL="http://ubuntuforums.org/showthread.php?t=2112271"]http://ubuntuforums.org/showthread.php?t=2112271
      [/URL]
 # Usually nVidia or AMD work with this:
nomodeset
# Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
# Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

    [URL="http://ubuntuforums.org/showthread.php?t=2112271"]
[/URL]

[URL="http://ubuntuforums.org/showthread.php?t=1911972"]
[/URL]

---

### Post by hans12345 on 2015-09-18
Thanks for your help and ideas, OldFred

Not much progress.
The Ubuntu installation still crashes at the end. The process  works just as a normal Ubuntu installation until the moment that it asks to restart the PC.  When I say yes, there is a brief flash of the purple  Ubuntu screen, then a black screen.
I have tried waiting for some hours to see if something is happening very slowly, but no. It has crashed. All I can do is to power off.

This is a simple PC, new, no additions. 1 HD, no Raid, no SSD.
The chipset is the standard Intel one on low end PCs, see:
[http://www.intel.com/content/www/us/en/chipsets/server-chipsets/server-chipset-3000.html](http://www.intel.com/content/www/us/en/chipsets/server-chipsets/server-chipset-3000.html)

This time I tried with Secure Boot off.  Legacy mode (here called CSM) is not enabled. But the Ubuntu  installation was the same. Except that at the beginning, I had a warning that the  PC was  "booting in an insecure mode". Then at the end, it crashed as usual with the black screen.
On restart, Win 10 boots as normal.
Note that I am using a USB Ubuntu Installation that has already worked on another PC (for a Win 10 / Ubuntu dual-boot), so the USB is a good one.

I did manage to look at the partitions  using parted -l :
dev sda
 sda1 NTFS 1048 MB
sda2  efi  272 MB (Boot, ESP)
sda3 fat32 524 MB (Windows Boot Mgr)
sda4 ---- 134 MB (MS reserved)
sda5 NTFS 262 GB
--
sda7 ext4 50 GB
sda8 ext4  150 GB
sda9 swap
sda6 NTFS 26 Win Recovery

I have recently discovered that there is an option in the UEFI BIOS for the ''Lenovo Service Engine'', which I am currently reading up on.
Currently this is enabled.

I have looked at OldFred''s links but I do not see anything there to help. I am still looking for a reason for the crash at the end of the Ubuntu installation.

Should my next step be to try:

[COLOR="#0000CD"]# Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60 # but change to your monitor size not 1280x1024
video=VGA-1:1280x1024-24@60 # but change to your monitor size[/COLOR]

Or try to disable the Lenovo Service Engine.
And should I try these variants starting with UEFI enable or disabled? Which is likely to be the best bet?

---

### Post by oldfred on 2015-09-18
Those are boot parameters to add to Linux line in grub menu. If you are not getting to grub menu then you cannot easily add those.

Can you press f12 or what ever key is the one time boot key to get into UEFI boot menu?

Besides Windows fast start-up or always on hibernation is another setting in UEFI that may be called fast boot or quick boot. That is separate from Windows setting. 

I have an Asus motherboard and it has two settings for fast boot, one from cold boot or full power down and the other is from warm boot or reboot. And I can set a boot delay, so I can have time to press key. I set normal boot on cold boot, so system does to full startup check of all devices. On reboot I set a 3 second delay and in grub a 3 second delay.

With a laptop you often have to remove battery and hold power switch for 10 sec to drain any remaining power to get a full cold boot. Then you may have time to press key to get into UEFI or one time boot key. And then or almost at same time press escape to get into grub.

---

### Post by hans12345 on 2015-09-19
> **oldfred said:**
> Those are boot parameters to add to Linux line in grub menu. If you are not getting to grub menu then you cannot easily add those.


Yes, no sign of Grub

> 
Can you press f12 or what ever key is the one time boot key to get into UEFI boot menu?


On my ACER, on which I recently was successful with your help in setting up a dual-boot, there was a f12 one time boot key.
With this Lenovo, there is no such thing.


> 
Besides Windows fast start-up or always on hibernation is another setting in UEFI that may be called fast boot or quick boot. That is separate from Windows setting. 

I have an Asus motherboard and it has two settings for fast boot, one from cold boot or full power down and the other is from warm boot or reboot. And I can set a boot delay, so I can have time to press key. I set normal boot on cold boot, so system does to full startup check of all devices. On reboot I set a 3 second delay and in grub a 3 second delay.

With a laptop you often have to remove battery and hold power switch for 10 sec to drain any remaining power to get a full cold boot. Then you may have time to press key to get into UEFI or one time boot key. And then or almost at same time press escape to get into grub.

The is a all-in-one desktop. When I power down, the PC is very much switched off. I have fastboot/quickboot off, and I now have tried both secureboot on and off.

I' ll try some more experiments and report back.

---

### Post by hans12345 on 2015-09-19
I tried with the Lenovo  Service Engine disabled.

No change.

This is taking a long time. Given that 98% of the time this PC will run Ubuntu, and Win 10 is only kept for obscure occasional use, should I consider Legacy mode? If it takes a couple of extra steps (e.g. bringing up the BIOS and changing options) then this will not be a problem.

How is this for a plan:

1 - I install Ubuntu in Legacy (actually CSM) mode. I hope this means it will not crash at the end of the installation.
If all is well and changing options in the BIOS allows me to (rarely) boot up Win 10, then I am happy. I do understand the Legacy implies an MBR and this limits me to 4 partitions, but this is enough.

2 - If this turns out not to work (maybe Win 10 will not start, etc), I use Boot-repair to do its magic and convert the Ubuntu from Legacy boot to UEFI boot.

How does this sound?

---

### Post by oldfred on 2015-09-19
If Windows is UEFI, you must install Ubuntu on the gpt partitioned drive. It can be  UEFI and grub and Windows share the ESP - efi system partition.
But Ubuntu can boot in BIOS/CSM/Legacy mode but for grub to correctly install you must have a 1 or 2MB unformatted partition with the bios_grub flag. Or if using gdisk it is code ef02.

I have both ESP & bios_grub on most drives as I started converting to gpt years ago for all new drives, but old system used bios_grub and new system only uses the ESP.

As long as you have both an ESP & bios_grub partitions Boot-Repair can convert from one boot to the other either way. UEFI or BIOS.

---

### Post by hans12345 on 2015-09-21
I feel quite confident with PCs and Win/Ubuntu/ChromeOS etc and have a good background in IT, but I just read the gdisk tutorial. This is getting scary. 

I am basically a cautious person and I do not want to end up with a bricked PC.

> **oldfred said:**
> If Windows is UEFI, you must install Ubuntu on the gpt partitioned drive. It can be  UEFI and grub and Windows share the ESP - efi system partition.
But Ubuntu can boot in BIOS/CSM/Legacy mode but for grub to correctly install you must have a 1 or 2MB unformatted partition with the bios_grub flag. Or if using gdisk it is code ef02.

Does this mean I need to setup a 2 MB partition before I start the installation?

> 
I have both ESP & bios_grub on most drives as I started converting to gpt years ago for all new drives, but old system used bios_grub and new system only uses the ESP.

As long as you have both an ESP & bios_grub partitions Boot-Repair can convert from one boot to the other either way. UEFI or BIOS.

Ill try this if I have to. But not yet.

My "progress'' since last time:
I set the Uefi/BIOS to CSM mode. Secure boot off. Quickboot off.
I started an install of Ubuntu again. This time of course with the warning ''Booting in insecure mode''
(this time I also tried with the install option for 3rd party SW, the option for non Open Source extras)

I took the first option, re-install Ubuntu, rather than the do something else path. It was a standard install, nothing special, and I saw the   ''please restart to complete installation'' msg.

Just as with all the previous installs, I saw a brief flash of the purple Ubuntu screen and then the black screen.

Exactly the same.

So, it seems I cannot install Ubuntu in CSM mode.

There is one change, after I power off and power on again. I see a very brief flash of CLI style messages, the last of which is something like ''Media Test Failure'' and then Win 10 boots as normal. (Remember, the BIOS is still in CSM mode)


I have to find out why the Ubuntu installation fails in its final ''restart'' step.

Any ideas?

---

### Post by oldfred on 2015-09-21
What video card/chip?
Even if you install in CSM mode from flash drive, you may still have UEFI on in UEFI/BIOS for hard drive. So then it does not find or boot a grub in the MBR.

In UEFI mode it goes thru the options of system to boot. And some brands only allow Windows to boot in UEFI mode. We have multiple work arounds for those systems. Not sure about Lenovo. One of the posts in post #4 above looks like he had to use a work around of renaming grub or shim to bootx64.efi in the /EFI/Boot folder for UEFI boot.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by hans12345 on 2015-09-22
I want to explain why I have not posted the  graphics chipset details.
Everywhere I look for the Lenovo C260 (with Celeron J1800 dual core CPU)  I am just told "Intel HD Graphics" .

I have found a quote from a post at Tomshardware which says:
Quote
To provide a little more clarity since "Intel HD Graphics" is a very generic term and it is used multiple times.
To begin, there is actually an "Intel HD Graphics" core with absolutely no model number like the 2000, 3000, 4000, etc. It represents the lowest performance graphics core for each generation. 
There are basically 3 different generations Sandy Bridge, Ivy Bridge and Haswell. each generation of the "Intel HD Graphics" core is more powerful than the previous generation. However, if you are not familiar with Intel's CPUs then you do not know which generation you are dealing with. I think the Haswell generation "Intel HD Graphics" core is almost as powerful as the Sandy Bridge generation Intel HD Graphics 2000 core.

To add to the confusion, there are basically two different CPU families that are developed by Intel. One family that most people are familiar with is Haswell which is the current generation CPU used for both desktops and laptops. However, there is a 2nd family of CPUs for entry level laptops and tablets who's main goal is to achieve decent enough performance with very low power consumption. These are known as Atom CPUs and the current generation is called Bay Trail.

Atom CPUs are much less powerful than the CPUs used in desktop / laptops. The Intel Celeron J1800 is an Atom CPU. The "Intel HD Graphics" core is derived from the Ivy Bridge generation "Intel HD Graphics 4000" core, but is much less powerful to keep power consumption low.
Unquote

---

### Post by hans12345 on 2015-09-22
Boot-repair report at 

[http://pastebin.ubuntu.com/12520062/]("http://pastebin.ubuntu.com/12520062/")

From the report, the conclusions:
=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of sda7, using the following options:        sda2/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s    use-standard-efi-file

=================== Final advice in case of suggested repair

If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\...\grub*.efi

End-quote

I already tried ''If your computer reboots directly into Windows, try to change the boot order in your BIOS.'' - It does boot to Win 10, but changing the boot order cannot be done.

---

### Post by oldfred on 2015-09-22
Did you try adding the entry to Windows BCD? That often works, but you boot into Windows & reboot into Ubuntu.
Other work arounds for those systems that will not recognize ubuntu entry. Same as in post #4. Also in link in my signature. Then boot a default hard drive entry. Most UEFI will create the entry, but you may have to reboot a couple of times or you can add a hard drive entry with efibootmgr.
       [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
            Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

Intel video does not work with nomodeset boot parameter, but other boot parameters are often required.
       
 # Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
# Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

---

### Post by hans12345 on 2015-09-25
OK I am a bit stuck  as to how to proceed. I need to do some studying of various alternatives.

But I am very busy with other things right now, so I expect I shall be offline for a week.

---

### Post by oldfred on 2015-09-25
Are you installing full Ubuntu or Lubuntu or Xubuntu?
Lightweight processor & video may work much better with the lighter weight versions of Ubuntu.

---

### Post by hans12345 on 2015-10-01
> **oldfred said:**
> Are you installing full Ubuntu or Lubuntu or Xubuntu?
Lightweight processor & video may work much better with the lighter weight versions of Ubuntu.

Thanks OldFred. As you see I'm back.

I am fairly sure my current problem is due to a failure of Ubuntu to install, so this is a good idea. 

I will try Xubuntu.

---

### Post by hans12345 on 2015-10-01
Finally, a 95% solution with Xubuntu. This means the Celeron J1800 CPU (which I have seen stated somewhere is just a jumped up Atom CPU) has such poor graphics that it cannot run Ubuntu !

Not a perfect solution, but this is my wife's new PC and she is getting impatient. She will only use Xubuntu and Win 10 will be possible if I want to use it. (Well, it is conceivably possible)

The setup:
I used an old Pendrive made USB with Xubuntu 15.04 (I say this because the Pendrive USB installer did not work with my ACER dual-boot, I had to use Rufus).
BIOS settings: Secure boot off, Quickboot off, CSM (legacy) enabled, Boot priority set to Legacy First.
Chose Allow 3rd party SW.
Chose option to Erase Ubuntu 15.04 and re-install.
Installation runs smoothly until ''Please restart to Complete Installation'' message. Then it is as before, except instead of the purple Ubuntu screen, then black, I get a blue Xubuntu screen, then black.
As usual, I am forced to power off, and power on again.

I expected that this was another installation failure. But Grub appeared ! And Xubuntu works.

But it still will not close down properly - I have to power down.

It is not a real dual boot, since I have used CSM and although Windows appears on the Grub menu, it will not boot.

So if I want Win 10 (well, it might happen one day), I enter the BIOS and set  CSM off, and the Win 10 boots (after a strange popup message to which I answer ''No'').

I imagine I could fix the dual-boot with Boot-repair, but my wife is waiting.

Thanks to everyone especially Old Fred, for your help.

I will close this thread in a couple of days if there are no further posts.

---

