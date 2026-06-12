---
title: "Ia there an UEFI switch in the 14.04 LTS distro?"
date: 2015-09-29
forum: Installation &amp; Upgrades
---

### Post by Boyntonstu on 2015-09-29
I need UEFI to boot on a Win 8.1 laptop.

Where, how does one get the option/switch/addon  to create a persistent  or an dual boot install USB?

---

### Post by ubfan1 on 2015-09-29
The live media installer works with either UEFI or legacy, depending upon how you set up your machine.  Persistence was fixed in 15.04 I think. See bug 1159016 for do it yourself instructions.

---

### Post by Boyntonstu on 2015-09-29
> **ubfan1 said:**
> The live media installer works with either UEFI or legacy, depending upon how you set up your machine.  Persistence was fixed in 15.04 I think. See bug 1159016 for do it yourself instructions.

Which live media installer?

Are you saying that the live media installer on a UEFI machine will install to that machine?

Are you implying that a portable USB stick cannot work on both legacy and UEFI?

At the  moment I have Lubuntu 14.04 installed and running fine on a 32 GB USB stick.

My UEFI laptop will not allow it to boot.

Please expand your first sentence.

Thanks

---

### Post by oldfred on 2015-09-29
If a full install to any external drive you have to manually partition with gpt and be sure to include the ESP - efi system partition.

And then you can only install with Something Else using live installer booted in UEFI mode.
       Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

    Post this:
sudo parted -l

You should specify to install grub to sdb or whatever external drive is. But if UEFI grub seems to only install to the ESP on your sda drive. You can disconnect all other drives, or copy files afterwards to sdb.
And you have to manually copy efi boot files into ESP. And then copy  again and rename shimx64.efi to (USB)/efi/boot/bootx64.efi. External  drives only boot from bootx64.efi in UEFI mode.

---

### Post by ubfan1 on 2015-09-30
Sorry for being unclear.  The downloaded Ubuntu isos when burned to CDROM or USB make a live media installer.  This is portable in the sense that is works with a variety of hardware, and works with both UEFI and legacy boots.  This might be what you are calling a portable USB, but since you say you "installed" to a 32G stick, it might also be a regular install from a live media installer to another stick.  The fact it doesn't boot seems to indicate that your 32G stick is a regular (non-UEFI) installation and not a live media installer.  
   It is possible to install to a sitck in UEFI mode, but there are a few pitfalls, as oldfred mentioned above.  The external boot device setup also needs a copy of grubx64.efi in /EFI/Boot if bootx64.efi  is a renamed copy of shimx64.efi  (That will work with or without secure boot).  The only other critical file is /EFI/ubuntu/grub.cfg, which gets written to the sda's ESP, and should just be copied over to the external device's /EFI/ubuntu.
  I tend to copy everything from the sda's ESP to the external device's ESP, since it makes for a convenient backup.  Really without an Ubuntu installation on the internal disk, it's pretty straightforward.   I have found that creating full install USB on a machine with Ubuntu installed on sda will sometimes mess up the nvram entries, replacing shim with grub or somesuch unnecessary and wrong change.  Putting the /EFI/Boot setup on sda has worked in a fallback when the nvram entry gets wrongly changed, so that's good to do.

---

