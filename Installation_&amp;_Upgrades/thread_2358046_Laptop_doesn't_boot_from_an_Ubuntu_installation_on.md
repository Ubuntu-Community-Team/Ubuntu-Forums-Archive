---
title: "Laptop doesn't boot from an Ubuntu installation on a flash drive"
date: 2017-04-09
forum: Installation &amp; Upgrades
---

### Post by ilikestuff on 2017-04-09
Hello there.

I installed Ubuntu 16,10 on a 16GB flash drive. I **used a separate flash drive as a live usb** for installing the system onto the 16 gigs flash drive.

I created just one partition on the drive (mount point= / ), and installed the bootloader onto /dev/sdb (which is the flash drive itself).

The installation went well and no errors were reported. I shutdown the system, removed the live usb, and then booted the laptop from the drive i used for installation. But the laptop just sits there with a blank screen doing nothing. It has been 35 minutes now. Any clues as to what might be wrong?


More information:
Laptop: HP DV6 6165tx 
CPU: Intel core i7 2670QM
GPU: Radeon 6770M

Also, i am trying to install Ubuntu on a flash drive because this laptop currently doesn't have a hard drive.

---

### Post by oldfred on 2017-04-09
I do not know AMD graphics.
What version of Ubuntu?
Have you installed in BIOS boot mode and is system then booting with CSM/Legacy on?

 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
[http://www.rodsbooks.com/efi-bootloaders/csm-good-bad-ugly.html](http://www.rodsbooks.com/efi-bootloaders/csm-good-bad-ugly.html) 

      
 16.04 Release notes
When upgrading to Ubuntu 16.04 from a previous release, both the fglrx driver and the xorg.conf will be removed, so that the system is set to use either the amdgpu driver or the radeon driver (depending on the available hardware).  

 [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)

---

### Post by ilikestuff on 2017-04-09
I am using Ubuntu 16.10.

The laptop bios does not have any options to configure CSM/Legacy mode.
I am not a 100% sure, but i think the laptop isn't a UEFI model. Is there any way to find out? 

Regarding the radeon graphics, the BIOS does not have an option to disable the discreet graphics. There are just two settings for the graphics card: Fixed and Dynamic (the laptop has switch-able AMD graphics).

I also tried installing fedora onto the flash drive, but it doesn't boot either.

EDIT: I should also add that it doesn't matter which setting i choose for the GPU (dynamic/fixed). Neither of the distros boot.

---

### Post by oldfred on 2017-04-09
May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Was system originally Windows 7 or Windows 8?
If Windows 8 then UEFI.

Some other HPs, may be similar issues?

 HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)

---

### Post by ilikestuff on 2017-04-09
I ran Boot-Info from a live-usb. Here is the output: [http://paste2.org/pAOycbnp](http://paste2.org/pAOycbnp)

The system was originally on Windows 7.

---

### Post by oldfred on 2017-04-09
The installed flash drive is not showing at all?
Just the installer.

Post this, does it show both flash drives?
lsusb

---

### Post by ilikestuff on 2017-04-09
The detection of flash drives is NOT a problem. Both the drives (live usb and installation drives) show up in lsusb and they work just fine.

The problem is that the laptop gets stuck while booting from the drive on which i installed Ubuntu.

Here a couple of more observations: 
1. The installation flash drive shows in the laptop's boot device options.
2. This means that the bootloader is installed correctly and the laptop is able to boot from it, because otherwise the laptop's BIOS would have displayed the message "No boot device found."
3. This also indicates then that the problem lies somewhere inside the booting process, and not in the installation process. Maybe some specific hardware config of this laptop isn't allowing ubuntu to boot? I'll try Ubuntu 14.04 LTS because it has support for the discreet GPU in the laptop.

---

### Post by yancek on 2017-04-10
> The problem is that the laptop gets stuck while booting from the drive on which i installed Ubuntu.

There is no way anyone here, even an expert like oldfred, will be able to help you with this because there is no information on the drive on which you installed Ubuntu in the boot repair output.  It only shows basic info on the installation usb.

> 1. The installation flash drive shows in the laptop's boot device options.

The drive that needs to show there is the one you installed Ubuntu to, not the one you installed from.  From the info you posted, there is no indication that Ubuntu was actually installed anywhere.

---

### Post by ilikestuff on 2017-04-10
> The drive that needs to show there is the one you installed Ubuntu to, not the one you installed from.  From the info you posted, there is no indication that Ubuntu was actually installed anywhere.

***The drive that shows up in the BIOS is the drive on which i installed Ubuntu. It is not the live USB i used to install the system. *****
****
> I have two flash drives.
> I used one drive to make a bootable Ubuntu USB.
> I used the other drive as a hard drive for Ubuntu installation.
> I booted into the live USB and selected the other flash drive as the installation drive. Bootloader was installed on this installation drive.
> Installation completed without any errors reported.
> I shut down the laptop.
> I removed the flash drive which contained Ubuntu live-usb. The drive which was used as a hard drive for installation was kept plugged in.
> Booted up the laptop, and went into BIOS to choose the boot device. [B][I]The flash drive that was kept plugged in (the drive on which i installed Ubuntu) shows up as a boot device.
[/I][/B]> I select that flash drive as the boot device and press enter. The BIOS screen disappears and the screen turns blank.
> Laptop stays this way forever.

I hope this clears up any confusion that might have crept up due to inability to express myself clearly.

---

### Post by oldfred on 2017-04-10
Rerun Boot-Repair with both flash drives plugged in.
We understand that flash drive with install is not booting, but need to see summary report, showing the flash drive with the full install so can see details.

But I do not know AMD graphics and what is current best way to deal with AMD. There are different versions of cards/chips and different versions of drivers that only work with some cards/chips.
You may be able to boot from install by adding nomodeset to linux line in grub. With one install grub menu will not normally show and you have to hold shift key from BIOS screen until grub menu appears.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by ilikestuff on 2017-04-10
Hey everyone, i appreciate you all helping me out with this frustrating issue. However, i have now gotten a hard drive into this laptop and Ubuntu 16.10 works very well. The flash drive installation problem just isn't worth spending more time on.

Thanks again! I will now mark this thread as closed.

---

