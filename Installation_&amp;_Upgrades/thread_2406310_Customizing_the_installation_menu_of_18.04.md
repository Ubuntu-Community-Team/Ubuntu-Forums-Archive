---
title: "Customizing the installation menu of 18.04"
date: 2018-11-19
forum: Installation &amp; Upgrades
---

### Post by rasmusson.stefan on 2018-11-19
I have earlier  built a custom install ISO with a customized the install menu for 17.10 server version. Now I'm trying to upgrade to 18.04 server version but running into some problems. 
On 17.10 the menu configuration was held in the isolunix folder menu.cfg and txt.cfg. In 18.04 there seems to be a new menu. The same files are still there in isolinux but changes in these does not reflect on the menu. The new menu seems to be based on some other files. I have tries searching the ISO for the words used in the menu shown but getting no hits. Does anyone know where the configuration fot this new meny are?

---

### Post by oldfred on 2018-11-19
The isolinux files are for BIOS boot.
Did you change to UEFI boot that uses grub to boot with /EFI/Boot/bootx64.efi as boot file for UEFI and then /boot/grub.

---

### Post by rasmusson.stefan on 2018-11-20
I run the installer in a VM guest and it is set to do BIOS boot. 
So you say the UEFI boot uses a installation menu from [COLOR=#000000]/EFI/Boot/bootx64.efi? [/COLOR]If I wanted do changes in the menu inside [COLOR=#000000]bootx64.efi, how would I go about doing that?[/COLOR]

The picture below is the menu Im getting.
[ATTACH=CONFIG]281706[/ATTACH]

---

### Post by oldfred on 2018-11-20
The menu is not in bootx64.efi, that is just the UEFI boot file.

It may be which server version you downloaded. There now are two.
       [https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes) 
            The next generation Subiquity server installer, brings the comfortable live session and speedy install of Ubuntu Desktop to server users at last.  
And with 18.04 the Subiquity was somewhat limited. That was improved with 18.04.1.

---

### Post by rasmusson.stefan on 2018-11-21
Right, as I understand the LTS version is the 18.04.1 So thats the one I have to use. Any idea on how to customize the menu for subiquity? Build from source? And in that case, where is the subiquity image stored on the ISO?

---

