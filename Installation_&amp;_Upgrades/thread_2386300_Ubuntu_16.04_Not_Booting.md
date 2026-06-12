---
title: "Ubuntu 16.04 Not Booting"
date: 2018-03-03
forum: Installation &amp; Upgrades
---

### Post by brewin95 on 2018-03-03
Ive been trying for days to fix this problem from reading other answers but none have worked. I am installing ubuntu from a USB stick once I install it and reboot it will come back up with:
Try Ubunutu
Install Ubuntu
Once I remove the USB stick it goes to reboot and select proper boot device 

Any help would be appreciated

---

### Post by thehipho on 2018-03-03
Were you able to Try Ubuntu? Could you give more detail about the computer your installing to?

---

### Post by brewin95 on 2018-03-03
I pressed install Ubuntu when through the installation restarted as it said but was taken back to the menu for try Ubuntu or install ubuntu
Laptop is a Toshiba satellite

---

### Post by oldfred on 2018-03-03
Is this a newer system with UEFI or older BIOS only system?

How you boot install media with newer systems UEFI or BIOS is then how it installs. But then you have to have system set to boot in that same boot mode.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by brewin95 on 2018-03-03
This is the link
[http://paste.ubuntu.com/p/nTf4VWMTJf/](http://paste.ubuntu.com/p/nTf4VWMTJf/)

---

### Post by brewin95 on 2018-03-03
Also it did let me use the try ubuntu option

---

### Post by oldfred on 2018-03-03
What brand/model system?

Run Boot-Repair, particularly to get the 'use the standard efi file'. That backs up bootx64.efi and copies shimx64.efi to be bootx64.efi.

Then we may need a fallback boot entry to boot /EFI/Boot/bootx64.efi.
Or if not using Windows an entry that says Windows but actually boots Ubuntu. 
Many systems violate UEFI standard that says not to use description as part of boot.

Various work arounds also in link in my signature. 

       Copy shimx64.efi to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others workarounds:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114](http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114)

Since you are only booting Ubuntu, you can use Windows description. From live installer in UEFI boot mode:


 **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

---

### Post by brewin95 on 2018-03-03
It is a Toshiba Satellite C50-B-14D
I dont have windows installed anymore as I wiped it for Ubuntu, so I'm not dual booting, I tried the boot-repair and I restarted, but didn't boot still only went to the menu where I can select try/install

---

### Post by brewin95 on 2018-03-03
It is now working from followong your instructions  it was to do with the efi, appreciate your help

---

