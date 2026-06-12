---
title: "Toshiba Satellite C855D-S5100 will not boot linux in UEFI mode"
date: 2016-02-04
forum: Installation &amp; Upgrades
---

### Post by WanderingAlbatross on 2016-02-04
Dear friends,

I hate to post as I find it very effective to search for answers to problems within what is already written.  I have dealt with a problem that even Rodsbooks, Oldfred and Yannubuntu, the UEFI legends, have written nothing on.
This Toshiba Satellite C855D-S5100 will not boot anything linux UEFI.  Not even live booting.  I tried many distributions: Ubuntu 14.04, Linux Mint Rebecca, three version of Boot-repair disk, Manjaro, Parted Magic, rEFInd.  None of them boot.  They will all show their Grub splash screens, then about two seconds after will lock up. (i.e. freeze, no alt-f2, no REISUB, no Num Lock, caps lock, whatever)  I have tried all from USB and at least 4 from LiveCD

They will, however, boot with no problems in CSM mode, as opposed to UEFI mode.

For a while I thought it was a graphics problem, but I tried everything I could think of: noacpi acpi=off nomodeset xforcevesa.  Even if this were the problem, why would it not be a problem in CSM mode? (a.k.a Legacy boot mode)

  Boot-repair is impossible to use unless you can get the system to boot into UEFI first.  It gives an error that the system is not in Legacy mode and please boot into UEFI mode first.  By the way, my results from a scan of the system are at [HTML]http://paste.ubuntu.com/14857715[/HTML]

I then tried Easy BCD 2.3 and their program says they can not allow installation of other operating systems because of it being against Microsoft's UEFI policy.

I then converted the Linux Mint system while already booted into Legacy mode because I was convinced that if I could just get there I would be okay.  Here are my commands for doing this:
```
sudo apt-get update
sudo apt-get install grub-efi
```

This removed grub-pc.

```
sudo modprobe efivars
sudo grub-install --target=x86_64-efi
sudo grub-install --uefi-secure-boot --target=x86_64-efi
sudo update-grub
```

With this I finally got the UEFI keys installed in the correct place.
However Windows booted normal, so:

```
sudo mount /dev/sda2 /boot/efi
sudo cp /boot/efi/ubuntu/* /boot/efi/boot/
sudo cp /boot/efi/EFI/ubuntu/* /boot/efi/EFI/boot/
sudo mv /boot/efi/EFI/Boot/bootx64.efi /boot/efi/EFI/Boot/bootx64.efi.backup
sudo mv /boot/efi/EFI/Boot/grubx64.efi /boot/efi/EFI/Boot/bootx64.efi
```

Then I found Windows still booted normally, so I had to change the same files in a Windows directory on the same /dev/sda2.

So I finally got what I wanted.  Of course, it wasn't booting Windows, but Boot-Repair will help, right?  So Grub shows up with the Linux Mint in the standard UEFI mode.  I clicked on it, and the same locked up condition happened!  I'm sure you have all met with this kind of disappointment before.

So here we have successfully proved that it is something with UEFI because this is the exact same system that was working before with legacy Grub.

My time ran out to play with this machine, so I taught the user how to switch between the two in the firmware, which is listed as InsydeH2O Rev 3.7.  This is not preferred.  The only avenue I have not pursued is updating the firmware.  I am writing now so that I can hear any ideas others might have for the time when I can get to this machine again.

---

### Post by ubfan1 on 2016-02-05
Have you updated the BIOS/firmware on that machine.  Some early ones had a misconfigured key database.  I think the insyder 6.60 fixed the problem.  Did you try with secure boot disabled? That might allow booting, but maybe only straight from grubx64.efi, not shimx64.efi.

---

### Post by sudodus on 2016-02-05
I have a Toshiba according to [this specification](http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/)

It was delivered with Insyde version 6.10. I have not changed it, and it works for me to boot in UEFI mode (with and without secure boot). I have used that computer to develop and test the tools/systems described in the following links,

[mkusb](https://help.ubuntu.com/community/mkusb)

[One pendrive for all PC (Intel/AMD) computers - single-boot dual-boot multi-boot](http://ubuntuforums.org/showthread.php?t=2259682)

[Portable installed system that boots in UEFI as well as in BIOS mode](http://ubuntuforums.org/showthread.php?t=2213631)

So I would recommend that you try to upgrade the UEFI/BIOS system to the newest version, that works in your computer, as suggested by *ubfan1*.

---

### Post by ubfan1 on 2016-02-05
There are two versions, one BIOS one firmware, e.g. from dmidecode output:
...
    BIOS Revision: 6.60
    Firmware Revision: 6.10
...
If you BIOS version is below 6.60, update it, the 6.50 had the problem.  Later releases are available, but I never needed to update as my machine came with 6.60.

---

### Post by WanderingAlbatross on 2016-02-06
Thank you both for your thoughts.  As I mentioned at the end of my initial post, that is the one thing I have not done yet.  I will work on the firmware when I get access to it again.

I don't blame anyone for this messy setup except Toshiba.  Even in this case I can't say it is a Microsoft conspiracy!

I did try with Secure Boot disabled as well.  In fact that is the only way it would get as far as it did.

---

