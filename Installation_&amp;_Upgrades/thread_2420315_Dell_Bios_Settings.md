---
title: "Dell Bios Settings"
date: 2019-06-03
forum: Installation &amp; Upgrades
---

### Post by angel mike on 2019-06-03
I have installed Ubuntu 14.04 using a USB stick on Dell Inspiron 3670 which had Windows 10.
How do I reset the bios to boot from the hdd?

---

### Post by CatKiller on 2019-06-03
Support for 14.04 has ended. It was released five years ago, hence the name. 16.04 or 18.04 would be significantly better choices.

The key to enter the BIOS is normally F2 for Dell machines.

---

### Post by angel mike on 2019-06-03
Thanks Catkiller for that speedy reply - the questions was aimed at the settings options.I know how to get into the bios but having changed to Legacy boot mode to load the USB and install the OS I cannot get back to booting from the hard drive. I will have to get Dell support as this is a new machine.  I waiting for a DVD of 18.04 - the 14.04 USB isofix is the only one I have at the moment.

---

### Post by dino99 on 2019-06-03
Why not getting it online ?  [http://releases.ubuntu.com/18.04/](http://releases.ubuntu.com/18.04/)

You probably can grab the bios boot option via F8 or F11 or similar (no Dell clue myself)

---

### Post by cruzer001 on 2019-06-03
Dell puts out their own version of 18.04.  Maybe thats what op is up to.

---

### Post by CatKiller on 2019-06-03
> **angel mike said:**
> I know how to get into the bios but having changed to Legacy boot mode to load the USB and install the OS I cannot get back to booting from the hard drive.

If you booted your install USB in Legacy mode, it will have installed in Legacy mode. That means that it won't be able to boot when not in Legacy mode.

There is more information than you could ever wish to know about the differences between the old BIOS (Legacy/Compatibility Support Module) and the more modern UEFI. If oldfred happens by, he seems to know all of it. For now, the important thing to know is that mixing-and-matching is problematic.

My advice would be to grab an iso of 18.04 (Kubuntu would be my personal preference) and install that in UEFI mode. Some very old USB drives can't be started in UEFI mode, so you might need to borrow a newer one if that turns out to be the case.

When Dell first started offering machines with Ubuntu - around 12.04, IIRC - they had some tweaks that they needed to apply. Those tweaks have been upstreamed now, so a standard modern install image should be fine.

---

### Post by angel mike on 2019-06-03
Thanks Catkiller and all that have replied. Comments are noted and will investigate further.

---

### Post by oldfred on 2019-06-03
If new system much better to use UEFI with gpt partitioning. All hardware since Windows 8 released in 2012 is UEFI based. BIOS/MBR is from original PC in middle 1980's with many kluges since to make it work with newer systems.

How you boot install media, is then how it installs. 
Lots of detailed info in link in my signature below and links to even more info. If questions post back.

Some other Dell 3000 series.
       Dell  Inspiron 3670 UEFI update & AHCI worked
[https://ubuntuforums.org/showthread.php?t=2412152](https://ubuntuforums.org/showthread.php?t=2412152)
Dell Inspiron 3567 Review i3 7100u (Works well)
[https://ubuntuforums.org/showthread.php?t=2364642](https://ubuntuforums.org/showthread.php?t=2364642)
Dell precison 3520 Turn off RAID & change to AHCI
[https://askubuntu.com/questions/1096492/installing-ubuntu-18-04-alongside-windows10-the-ssd-is-not-recognized](https://askubuntu.com/questions/1096492/installing-ubuntu-18-04-alongside-windows10-the-ssd-is-not-recognized)

---

### Post by angel mike on 2019-06-03
I have had a close read of the instructions on the Dell bios and oil does not give you an option to boot in UEFI mode if you want to use an external device - only Legacy.

---

### Post by angel mike on 2019-06-03
Looking on the Dell support site there is a way of changing the bios setting to enable UEFI to be used to boot a USB but this has to be done through Windows - so I will have to use the recovery tool to re-install Windows 10

---

### Post by oldfred on 2019-06-03
Are you sure?
My older Dell booted fine using f12 and choosing UEFI:xxxx where xxx was name or label on flash drive.
And many others with various Dell systems have booted both live installer and full install to external drives.
Dell sells many models that are only Ubuntu and newer Dells allow UEFI updates from Linux.

       UEFI/BIOS updates brand model list  for Dell with (uefi >= 0.6.2 & dell >= 0.7.3) 
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
fwupx64.efi
[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

---

### Post by jglen4902 on 2019-06-04
> **angel mike said:**
> I have installed Ubuntu 14.04 using a USB stick on Dell Inspiron 3670 which had Windows 10.
How do I reset the bios to boot from the hdd?
Have you looked at [this]("https://www.dell.com/support/article/us/en/04/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled-windows-10-8-1-8?lang=en")?  This particular article discusses adding a boot device that is not listed - in this case a CD/DVD.  However, it starts with a discussion of setting boot order in general.  It also shows disabling Secure Boot.

It seems like the Dell UEFI behaves just like most others.  You can set it to UEFI, then set Secure Boot to Disabled, then select/change the boot sequence.  It should not require a re-install of Windows, or anything else.  In most cases Legacy boot is not needed fo a Linux install from a USB device and should only be chosen as a last resort.  But a Disabled Secure Boot setting, and then setting the boot order is most often the keys to a successful Linux install.

Again, it appears that Dell UEFI is no different, but maybe I'm missing something.

---

### Post by &amp;wP*!) on 2019-06-10
Also worth mentioning to update the laptop firmware. It can have a lot of fixes & updates which can solve most of your problems.
[Check this]("https://www.dell.com/support/home/de/de/dedhs1/product-support/product/inspiron-3670-desktop/drivers")

---

