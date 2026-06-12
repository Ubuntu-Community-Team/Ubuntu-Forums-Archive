---
title: "Grub installed but does not boot"
date: 2019-08-26
forum: Installation &amp; Upgrades
---

### Post by je06 on 2019-08-26
I installled lubuntu along side of my Windows 10 installation the other day and I just used the install along side Windows option. It installed just fine but when I reboot, I boot into Windows. I went to my BIOS and made sure secure boot was off and that I was in UEFI boot mode. Windows was still the thing that booted. I reinstalled lubuntu but that didn't work. I ran boot-repair in lubuntu and bcdedit in windows. Nothing works. I only have one hard drive.

---

### Post by oldfred on 2019-08-26
What brand/model system?
What video card/chip?

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by je06 on 2019-08-27
Computer brand/model: HP Laptop 15-bs2xx
Video card: Intel UHD Graphics 605
Boot-info: [http://paste.ubuntu.com/p/9Pg3MZF6mT/](http://paste.ubuntu.com/p/9Pg3MZF6mT/)

---

### Post by oldfred on 2019-08-27
Have you updated UEFI from HP?
Many with HP have said that has solved many issues.

HP historically violated UEFI spec that says NOT to use description as part of boot. And only valid description was "Windows Boot Manager".

Does your Ubuntu boot using the hard drive entry, or is that just for the old BIOS boot (which you do not want).

Boot-Repair also for HP adds all the .efi boot files in the ESP as new grub entries in 25_custom. If you run Boot-Repair you can edit or even turn off execute bit on 25_custom to have only the entries you want.

       # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also. also can turn off execute on 25_custom if none wanted
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub

---

### Post by je06 on 2019-08-27
I just updated my UEFI but that did not solve my problem. I'm not sure what you mean by > [COLOR=#000000]Does your Ubuntu boot using the hard drive entry[/COLOR], but if I go into the advance boot options, I can select boot from another device and select lubuntu from the list and it boots grub and lubuntu just fine

---

### Post by oldfred on 2019-08-27
Some live with that way to boot.

UEFI boots external drives from /EFI/Boot/bootx64.efi. And UEFI years ago added that path/file to internal drives as a fallback boot. Usually shown as just a hard drive UEFI boot entry.
A few Windows installs have bootx64.efi be a copy of Windows .efi boot file and use that as default.
Grub now copies its shimx64.efi to bootx64.efi, so any fallback or harddrive boot entry will also work.

Some with HP have also said that changing boot order with efibootmgr (which grub also uses to make it first), does not work, but you can in HP's UEFI change boot order and that may then work.

---

### Post by je06 on 2019-08-28
Thanks for your suggestions. Unfortunately, none of these work. When ever I made a change with efibootmgr and restarted, my firmware ignores the new boot order and resets it back to it's original value. What I did to get around this was to move /EFI/Microsoft/Boot/bootmgfw.efi to /EFI/Microsoft/bootmgfw.efi and copy /EFI/ubuntu/grubx64.efi to /EFI/Microsoft/Boot/bootmgfw.efi. This tricked my firmware into thinking it was booting Windows but it was really booting grub. After this, I edited my grub configuration file to point to the real Windows boot loader.

---

### Post by oldfred on 2019-08-28
That was an old workaround we did.
But grub only boots working Windows. So when Windows updates turn fast start up back on, or a Windows update resets /EFI/Microsoft/Boot folder, your grub will not work.

Most with updated HP software have said using efibootmgr still does not work, but changing boot order from within UEFI does work.

If you keep your configuration, be sure to have both the Windows repair flash drive and Ubuntu live installer flash drive handy. That way you can reset UEFI settings if need be.

---

