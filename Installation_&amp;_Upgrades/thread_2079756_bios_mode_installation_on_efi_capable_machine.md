---
title: "bios mode installation on efi capable machine"
date: 2012-11-02
forum: Installation &amp; Upgrades
---

### Post by mzrk7 on 2012-11-02
I would like to install ubuntu 12.10 on an efi capable laptop, but since efi brings on this laptop much more issues than advantages, I would like to install it in bios mode. If possible I would prefer to use grub 1.99 rather than grub 2. Can anybody help me? 

My laptop is an acer aspire 5560. Processor is an amd a4-3300m with integrated ati 6480g.

Things I tried to do: 
1 plain, regular installation: ubuntu installs and I can boot it, but I can regularly shutdown it only every 2 times.
2 installation with a live usb in which I cancelled the efi directory. It installs, but when I reboot I only get a purple screen.

---

### Post by darkod on 2012-11-02
Did you also disable UEFI boot in the bios?

When installing in legacy mode, make sure you boot the cd or usb in legacy mode too, not the uefi device it shows in the options.

---

### Post by mzrk7 on 2012-11-02
how can I boot in legacy mode? My bios by the way doesn't give me options in enabling or disabling uefi boot. But I know for experience that I can install several distributions in bios mode.

---

### Post by darkod on 2012-11-02
On boards that support uefi, the dvd-rom for example will exist as two different boot devices. One will be the standard bios legacy boot, and the other will say like uefi dvd-rom or similar.

To install in bios mode the ubuntu cd (the dvd-rom) has to be booted in legacy mode, not in uefi. If the uefi device is booted the installer will try to install grub-efi and not grub-pc (normal grub2).

If your computer offer a boot menu by pressing F12 or another button during boot, it's best to use that, then look in the boot devices list and select the dvd-rom or the usb-hdd (if you are using bootable usb stick) that is in legacy boot, not uefi.

It would have been better if the board offered the option to disable uefi but if it doesn't you should still be able to install in legacy like you say, only make sure which boot device you select.

---

### Post by AlexDudko on 2012-11-02
Version 1.99-21ubuntu3 of grub is grub2 for Ubuntu-12.04 updated to 2.00-7ubuntu11 in Ubuntu-12.10. So  they are all grub2.
Though it's possible to install legacy grub:
> sudo apt-get install grub
This command will also remove grub2 from your system.

Disable EFI support in bios and install Ubuntu in the usual way. EFI doesn't give you any enhancements and additional security.

---

### Post by oldfred on 2012-11-02
Boot-Repair has the capability to convert a BIOS Ubuntu install to a efi Ubuntu install. I do not think it can go the other way but then it is possible to manually convert.

You would need a bios_grub partition with gpt partitioning for grub to install to MBR correctly, edit out the efi partiton in fstab and uninstall grub-efi and install grub-pc for the BIOS version to install to the MBR instead of the efi partiton.

---

### Post by mzrk7 on 2012-11-02
@oldfred I already partitioned my hard drive as mbr. From live cd I tried to install grub-pc but it failed
@darkod I can't see the installation devices doubled. I only get an efi based installation if I don't edit the live usb/dvd.

---

### Post by mzrk7 on 2012-11-02
I finally managed to install grub pc from live cd. Now I can use ubuntu. Even if it's the only OS installed, I can't see the grub menu. Do you know if there is any way I can get it?

---

### Post by darkod on 2012-11-02
When you have only ubuntu the grub menu doesn't show which makes sense since there is no other OS to select. If you need it sometimes you can get it by holding Shift during boot, after the bios POST ends.

In the grub config files you can configure it to show always but that would just slow your boot while waiting for the counter. it's better to leave it hidden and use Shift when you need it.

---

### Post by mzrk7 on 2012-11-02
ok, thank you very much!

---

