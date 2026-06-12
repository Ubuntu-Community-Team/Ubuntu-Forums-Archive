---
title: "Booting to install DVD resulting in garbled text"
date: 2012-05-16
forum: Installation &amp; Upgrades
---

### Post by Boyo17 on 2012-05-16
I am having trouble booting to the ubuntu install DVD.

I downloaded the 64-bit version of the install iso from [here]("http://www.ubuntu.com/download/desktop").  I burned that to a DVD and rebooted my computer.  I opened the BIOS boot menu and selected my DVD drive.  I briefly saw the following message:

error: "prefix" not set

Then I see the attached garbled text.

It looks like the installer is not using the correct video mode.

If it's relevant, I'm installing on a Lenovo IdeaPad Z570 with Windows 7 Home Premium installed.  I've tried this on both the laptop screen and an external monitor.

Has anyone encountered this?  Thanks!

---

### Post by hazrpg on 2012-05-22
**OP:** It might be worth changing the subject to include "Lenovo IdeaPad Z570".

I just recently bought a Lenovo IdeaPad Z570 too, and have the same issue. However I tried using Ubuntu 12.04 (amd64) Desktop/LiveCD (CD version).

Tried booting from USB, with no joy... but this could be because one of two things: Either a) the configuration used for the bootable USB drive I have*****; or b) the fact that the Lenovo z570 has an (U)EFI BIOS, and this bootable USB was created (tested and working) on a regular BIOS (legacy) system.

-----
**If it helps, this is what I know about the laptop:**
**-** Contains a (U)EFI instead of a legacy BIOS. This is based on information found on the internet (e.g. Lenovo Forum).
**-** Contains 4 partitons: 200MB (NTFS, System, Active, Primary), 654.69GB (NTFS, Boot, Page File, Crash Dump, Primary, Contains Windows 7), 29GB (NTFS, Logical, Contains Drivers/OEM Apps, Label: LENOVO), 14.75GB (unknown filesystem, OEM Partition, used for OneKey Recovery).
**-** Windows 7 Home Premium 64-bit (OEM) is preloaded.
**-** Despite using (U)EFI, Windows is preloaded in legacy mode! This is checked using a tool called "bcdedit" in Windows 7 which results in the "Windows Boot Loader" saying the path is "\windows\system32\winload.exe", this should show "winload.efi" if it was booted in EFI mode.
**-** The HDD is partitioned using MBR instead of GPT.

**-** Some of the Specs.:
 + Intel Core i7-2670QM (2.20GHz)
 + Intel HD Graphics 3000
 + nVidia GeForce GT 540M
 + CUDA/Optimus configuration graphics.
 + 750GB HDD
 + 6GB RAM
-----

**Side Note:** I have a feeling the CUDA/Optimus configuration is where the problem lies, however I must point out that I did change this in the (U)EFI/BIOS/CMOS from Optimus to Internal. Neither way allows me to boot the CD without the garbled text.

*****Configuration of the bootable USB drive:
- Ext3 filesystem.
- Bunch of ubuntu iso files (i.e. 10.04 to 12.04, both i386 and amd64) in a subdirectory called "iso". This is so I can install it anywhere, anytime, or to use as a LiveUSB on any machine for diagnostics, tweaks or fixes.
- Grub2 bootloader.
- Chain-loading the iso files (or iso loopback).
- grub.cfg manually configured each time a new iso is added.

---

### Post by anur.bhargav on 2012-05-23
> **Boyo17 said:**
> I am having trouble booting to the ubuntu install DVD.

I downloaded the 64-bit version of the install iso from [here]("http://www.ubuntu.com/download/desktop").  I burned that to a DVD and rebooted my computer.  I opened the BIOS boot menu and selected my DVD drive.  I briefly saw the following message:

error: "prefix" not set

Then I see the attached garbled text.

It looks like the installer is not using the correct video mode.

If it's relevant, I'm installing on a Lenovo IdeaPad Z570 with Windows 7 Home Premium installed.  I've tried this on both the laptop screen and an external monitor.

Has anyone encountered this?  Thanks!

The "error: prefix not set" is excatly the same problem even I'm facing on my Lenovo Z570, which I bought a few weeks back. I've made 2 CD's and one pen drive to rule out any CD burning/ Image errors. 
Also the options are 
1. Try Ubuntu without Installing.
2. Install Ubuntu. 
3. I'm not able to figure out what it is. 
And I think my laptop run BIOS and not UEFI, I figured this out by getting into setup (Pressing F2) during boot up.

Further more, I also installed Ubuntu twice and faced Grub Bootloader issues. Which I was able to fix the 1st time and unfortunately I had to do a one key recovery, and had to install Ubuntu again.
I googled and found an alternative solution  than what I used the 1st time to recover grub, but sadly the Grub Bootloader has NO UBUNTU IN IT. :P

---

### Post by hazrpg on 2012-05-25
> **anur.bhargav said:**
> The "error: prefix not set" is excatly the same problem even I'm facing on my Lenovo Z570, which I bought a few weeks back. I've made 2 CD's and one pen drive to rule out any CD burning/ Image errors. 
Also the options are 
1. Try Ubuntu without Installing.
2. Install Ubuntu. 
3. I'm not able to figure out what it is. 
And I think my laptop run BIOS and not UEFI, I figured this out by getting into setup (Pressing F2) during boot up.

Further more, I also installed Ubuntu twice and faced Grub Bootloader issues. Which I was able to fix the 1st time and unfortunately I had to do a one key recovery, and had to install Ubuntu again.
I googled and found an alternative solution  than what I used the 1st time to recover grub, but sadly the Grub Bootloader has NO UBUNTU IN IT. :P

anur.bhargav, I know for a fact its definitely a UEFI system, not a BIOS/legacy system! I booted "Acronis True Image Home" several times, and in the initial bootloader selection it states that it was booted in EFI-mode. So no questions about it the Z570 (or at least the one I have) is a UEFI system. The UEFI *looks* like a legacy BIOS, however if you notice at boot the bar at the bottom right is in more colour detail then your average BIOS... its also a progress bar! I've never seen that on a legacy BIOS (someone correct me if I'm wrong).

Just thought I'd keep you guys posted on what I've done so far...

Firstly, I've posted the question up on askubuntu.com [here]("http://askubuntu.com/questions/141171/garbled-text-on-12-04-live-cd-during-installation-on-lenovo-z570"). Noticed anur.bhargav that you've already posted on there too!

anur.bhargav, you are right with option 1) and 2). I've managed to actually see them now, the options are:

1) Try Ubuntu Without Installing
2) Install Ubuntu
3) Check Disc For Errors

Right, now you might ask how did I go from garbled to being able to see them? Let me explain what I've done, not sure if this is repeatable... but here goes:

TL;DR: Note, I was able to boot the CD into "Try Ubuntu" after doing all of this! Flash BIOS (**PLEASE SEE WARNING BELOW!**), successful, still garbled. Tried USB, still won't boot from USB. Entered UEFI/BIOS, picked the reset to defaults option, restarted, entered UEFI/BIOS again, changed boot order, booted CD, worked! Didn't install Ubuntu yet out of fear of the unknown, but boots and works!

_**WARNING:** Quick heads up for those willing to try this._ Flashing may brick your system, or stop the system from booting. Not sure if Lenovo has a system in place whereby if you put in a USB device with a BIOS ROM on the root of the drive, it will flash it on... but I know most boards recently have started doing it... but can't guarantee that Lenovo do this! However I've never had a problem ever flash the BIOS on any machine in the last 10 years (and I've used many different methods! And many different types of machines!)... I still feel I need to warn you though!

I was annoyed by the fact that the boot order wouldn't save in the UEFI/BIOS... so I went onto the Lenovo website, and grabbed the latest version of it which says it fixes it (along with other bugs).

Installed the UEFI/BIOS in Windows (since its a Windows executable). Its meant to allow you to backup first before flashing, however when I opened it, it didn't give me this option it went straight to flashing. Then after it flashed, allowed me the option of picking either backup or flash. So quick warning there! For those that know what they're doing, you can alternatively extract the ROM straight from the executable (using 7-zip or similar), and use your own tool if you wish (not recommended, if you've not done this before). My issue might have been because it asked for admin rights on execution, and I accepted (tut tut on my part but oh well)... so declining might stop it flashing straight away, but not sure on that one!

After I flashed, rebooted, and hopped straight to trying to boot the CD again. Still no joy, text is still garbled, no option lets me continue, still get the same error message before seeing the list of options. Tried again with USB... still won't let me boot from USB. Could just be an unsupported company/device (reference: its a SanDisk Cruzer - 8GB).

Decided that the next step should be to reset the UEFI/BIOS to the new default settings provided with the new ROM... so booted into the UEFI/BIOS and reset to defaults, and rebooted.

Went into the UEFI/BIOS again to change the boot order (I always prefer it to be USB:FDD, USB:HDD, USB:CD, CD/DVD, HDD, Network, so this is the one I used for reference).

Proceeded to boot from CD again! This time it worked! I could now see the text clearly! All options worked flawlessly! Messing around in ubuntu, it seems to have booted fine. Haven't checked to see if it was booted in UEFI-mode or legacy yet, but it worked! Rebooted several times, to make sure it wasn't a fluke (lucky). All reboots checked out fine. Even tried resting the system for a while, and trying again... still visible, still booting all options! Nice! So we have progress. Note: Tried booting off the USB again, no joy! So must be an incompatible device for booting off. Might try and get a new one (*le sigh*).

I would like to quickly point out, although I got it to boot, I still haven't tried installing it yet. Still want to make sure that I have everything prep'ed up in case anything goes wrong along the way. (e.g. backups, Windows 7 disc, OneKey Recovery disc backup, Ubuntu disc, grub fix bootable disc, android phone, clonezilla disc, etc, etc, etc... I'm a paranoid guy!)

---

### Post by hazrpg on 2012-05-25
Forgot to metion, the error "error: prefix not set" still shows up however.

**EDIT:**
Also, if the solution above works for you, please state so either here on the forum (or better yet both) on the [ask ubuntu]("http://askubuntu.com/a/142285/10857") question I opened. I'm posting my solution up as an answer, but please let me know if it works for you before I mark it as a true answer (green circle/ticked/solved/etc).

---

