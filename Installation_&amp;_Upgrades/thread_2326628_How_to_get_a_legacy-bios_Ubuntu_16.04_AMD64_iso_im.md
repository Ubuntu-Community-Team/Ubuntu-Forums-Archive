---
title: "How to get a legacy-bios Ubuntu 16.04 AMD64 iso image?"
date: 2016-06-02
forum: Installation &amp; Upgrades
---

### Post by rlynwood on 2016-06-02
Hello,

I've partitioned a new, low-end Asus computer's 1T hdd and want to install Ubuntu 16.04 AMD64, legacy-bios version, into one of its partitions.  The computer came with Windows 7 Home Premium and a default legacy bios setting.  But the iso image I have, the default one, seems to be only for a UEFI installation.  How do I get an iso for a legacy-bios version of Ubuntu 16.04, AMD64?

Regards,
Ray

---

### Post by Mark Phelps on 2016-06-02
Where did you get the image from?

Asking because I recently installed Ubuntu 16.04 64-bit and it's on a BIOS-only desktop, not UEFI, and it went without a hitch.

---

### Post by sudodus on 2016-06-02
I agree with Mark Phelps. The official Ubuntu iso files work in both UEFI and BIOS mode.

Maybe your problem is caused by the method or tool, that you use to create the boot media. Are you booting from a USB pendrive?

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by ubfan1 on 2016-06-02
Some machines have settings for both legacy and UEFI boot, with an order selection you can change.  Maybe it just has UEFI before legacy, and since the install-media is both, UEFI was selected.  Turn off CSM, that allows the machine to pick which way to boot, and may be wrong for you.

---

### Post by rlynwood on 2016-06-03
Thank you all.  I put the image on a usb pen/flash drive and tried to install it from that.  Asus's version of American Megatrends' bios does indeed accommodate both legacy and UEFI formats, and in had Windows 7 Home Premium installed with the bios set to CSM.  I further put flash drive at the beginning of the boot order, followed by the optical drive, then the hdd.  But it still hangs up, attempting to install the UEFI form.  This happened in my earlier attempt; I guess I'll try once again.

---

### Post by grahammechanical on 2016-06-03
If Windows 7 is installed in CSM mode then Ubuntu must also be installed in CSM mode. And we do that by running the live session in CSM mode. I have noticed that a USB stick with an operating system on gets detected by my BIOS motherboard as an external USB drive and I set not the boot priority as you have done but the hard drive to boot from under a different setting in the BIOS/UEFI settings utility.

On my machine setting the boot priority works when using a DVD disc but setting the boot drive works when using a USB stick. It might be something similar with your BIOS/UEFI boot system.

Regards.

---

### Post by sudodus on 2016-06-03
1. Did you check the md5sum of the iso file? That way you can make sure that the download was successful.

2. Please tell us how you created the USB boot drive. Which tool did you use? For example, all versions of the Ubuntu Startup Disk Creator before Ubuntu 16.04 LTS have problems to make pendrives boot in BIOS mode. Tools that clone the iso file to the pendrive are much more reliable.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

3. What happens if you boot with the pendrive inserted, and enter the UEFI/BIOS menu system? Can you see the pendrive as one of the hard disk drives? In that case, please put it at the top of the list, and maybe you will be able to boot. See this link

[FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

---

### Post by rlynwood on 2016-06-05
1.  Originally, after downloading the iso's, yes.  After that, I've just installed that iso onto the flash drive and done that a number of times because I've used the same drive to install Kubuntu onto one partition and attempted to install Ubuntu onto another partition.  I've also used the Ubuntu Live image to work on the hdd with Gparted.  Kubuntu worked, but Ubuntu hasn't so far.
2.  First, I used Mint 17.1's KDE, Version 4.14.2,'s USB Stick Formatter to format the drive as ext4, then its USB Image Writer to put the Ubuntu 16.04 iso onto the drive.  I saw nothing in the link you provided here that addressed the creation of a legacy-bios-based Ubuntu 16.04 image on a flash drive.  Perhaps I missed something.  And it didn't address such a creation with the KDE tool.
3.  American Megatrends' ASUS bios gives two categories of options:  (1) click on the EZ BIOS(?)'s boot link in the lower right corner, yielding a bootable item list I can select by clicking, and (2) click its Advanced BIOS (incorrect wording) setup section, click on the boot tab, then scroll down to the boot order entry and make the pendrive the 1st boot option.  Alternatively, I can scroll down a bit farther to the hdd boot-order entry, click it, and make the pendrive the 1st boot option.  I think I've done both, but in one of those options, I believe that there is no legacy-bios option, only the UEFI version of the pendrive.  That, together with the fact that it doesn't boot, is what makes me think that the image is UEFI only.

Thanks for all this thoughtful input.  I'll really appreciate your followup help.

---

### Post by oldfred on 2016-06-05
There are three ways to boot new UEFI systems:
UEFI with secure boot, standard UEFI and BIOS/Legacy/CSM.
And flash drive and once installed may not have same default settings to boot.

Normally if flash drive is standard Ubuntu image it is in a FAT32 formatted partition with boot flag. And then syslinux is installed for BIOS boot.
That flash drive then will show in UEFI boot options as UEFI:flash drive or just flash drive for BIOS.
If Secure boot turned on in UEFI, then only UEFI Secure boot will be a boot option, as both standard UEFI and BIOS/CSM are not secure boot.

Some other ways to create flash drive:
 [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
these should then work:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[URL="https://wiki.ubuntu.com/Win32DiskImager/iso2usb"]https://wiki.ubuntu.com/Win32DiskImager/iso2usb
[/URL][http://unetbootin.github.io/](http://unetbootin.github.io/)

---

### Post by sudodus on 2016-06-05
If you ***clone*** an Ubuntu family 64-bit iso file to a USB pendrive, it can boot both in UEFI and BIOS mode.

You can do it with [mkusb](https://help.ubuntu.com/community/mkusb) and also other tools, that use the cloning method (copy each byte directly from the iso file to the pendrive). This corresponds to burning an iso file to a boot CD or boot DVD. (There are other methods, that are more complicated and therefore more likely to fail.)

If Kubuntu works, Ubuntu (of the same version, for example 16.04 LTS or 14.04.1 LTS) should also work. They use the same kernel and drivers under the hood.

-o-

I suggest that you try all the options in the UEFI/BIOS menu system systematically. Take notes, so that you need not test the same combination of settings twice. Finally, read *oldfred*'s tips very carefully, I'm rather sure they will help you find a solution.

---

### Post by rlynwood on 2016-06-05
Thank you both.  I'll do as you say and get back after I have some definitive answer, likely in a day or two.  Thanks, again.

---

