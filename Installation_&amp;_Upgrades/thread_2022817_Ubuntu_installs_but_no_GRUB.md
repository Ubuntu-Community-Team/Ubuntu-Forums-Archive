---
title: "Ubuntu installs but no GRUB"
date: 2012-07-11
forum: Installation &amp; Upgrades
---

### Post by razzmataz1478 on 2012-07-11
Hi 

I have already installed ubuntu before onto my laptop and everything was fine.

Today I got a new PC, an Advent DT1411, and have gone through the process of installing this to dual-boot with Windows 7.

Installation went fine, and after was prompted to restart, so obviously I did.

But...

my PC booted straight into windows, no sign of GRUB whatsoever.

Can anyone help me get GRUB please, or is there a way where my flash drive could trigger the boot into the ubuntu partiton?

Thanks 

Ryan

Just for the record, I installed Ubuntu from a USB drive.

---

### Post by Version Dependency on 2012-07-11
You'll need to use a live CD and then run the boot repair tool: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


From there, you can install GRUB to any partition.

---

### Post by razzmataz1478 on 2012-07-12
> **Version Dependency said:**
> You'll need to use a live CD and then run the boot repair tool: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


From there, you can install GRUB to any partition.


I have tried this, but when adding the repo I just get stuck on the cursor.

I also tried the live-cd (using a cd) but couldn't get an internet connection.

Anything else I can try?

---

### Post by dino99 on 2012-07-12
is that new pc using a bios or uefi ?

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by razzmataz1478 on 2012-07-12
> **dino99 said:**
> is that new pc using a bios or uefi ?

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

I'll have a look, thanks!

---

### Post by Version Dependency on 2012-07-12
> **razzmataz1478 said:**
> I have tried this, but when adding the repo I just get stuck on the cursor.

I also tried the live-cd (using a cd) but couldn't get an internet connection.

Anything else I can try?

You could download an ISO of a live CD with the boot repair tool already on the disc: [http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

### Post by drs305 on 2012-07-12
Have you tried booting with the USB device you installed Ubuntu from still attached? It's possible GRUB's boot information was installed on the external device, even though it would point to the internal drive's Ubuntu files.

If the USB device isn't available, BIOS would try booting sda's MBR information, which might still point to Windows.

---

### Post by razzmataz1478 on 2012-07-12
> **razzmataz1478 said:**
> I'll have a look, thanks!

In the BIOS(?) I did find some references to UEFI so I think this may be the problem...

---

### Post by razzmataz1478 on 2012-07-12
> **Version Dependency said:**
> You could download an ISO of a live CD with the boot repair tool already on the disc: [http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

This is what I meant when I said 'live-cd'

---

### Post by razzmataz1478 on 2012-07-12
> **drs305 said:**
> Have you tried booting with the USB device you installed Ubuntu from still attached? It's possible GRUB's boot information was installed on the external device, even though it would point to the internal drive's Ubuntu files.

If the USB device isn't available, BIOS would try booting sda's MBR information, which might still point to Windows.

Booting from USB brings up the installation GRUB

Try Ubuntu without installing 
Install Ubuntu
(That other option that I can't remember!)

---

### Post by razzmataz1478 on 2012-07-12
> **dino99 said:**
> is that new pc using a bios or uefi ?

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

Sigh. Is there not an easier way of booting using UEFI? Building GRUB etc. I just don't know if I can be bothered to do that.

---

### Post by drs305 on 2012-07-12
Are you using UEFI/EFI booting? 

I'm not knowledgeable enough about EFI booting to provide instructions. If you are using a normal BIOS/MBR boot you could boot the LiveCD and then install GRUB to the sda MBR. 

However, without an Internet connection, I'm not sure I'd recommend it at this point since you will lose your Windows bootloader in the process. With an Internet connection you could restore the Windows bootloader easily via the LiveCD, but without it you would be stuck with no OS if GRUB still didn't work.  :-(

---

### Post by razzmataz1478 on 2012-07-12
> **drs305 said:**
> Are you using UEFI/EFI booting? 

I'm not knowledgeable enough about EFI booting to provide instructions. If you are using a normal BIOS/MBR boot you could boot the LiveCD and then install GRUB to the sda MBR. 

However, without an Internet connection, I'm not sure I'd recommend it at this point since you will lose your Windows bootloader in the process. With an Internet connection you could restore the Windows bootloader easily via the LiveCD, but without it you would be stuck with no OS if GRUB still didn't work.  :-(

I think that I'm using UEFI anyway....

Just found this: [http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Secure_Boot](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Secure_Boot)

Do you think it's worth giving it another shot if I turn off secure boot?

---

### Post by YannBuntu on 2012-07-12
Hello

Boot-Repair-Disk is based on Debian stable, so it may difficult to connect internet because of its old drivers.

Instead, you can use Ubuntu-Secure-Remix, which an Ubuntu 12.04 with pre-installed Boot-Repair.

See [https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

