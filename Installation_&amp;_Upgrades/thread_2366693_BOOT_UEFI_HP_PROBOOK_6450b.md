---
title: "BOOT UEFI HP PROBOOK 6450b"
date: 2017-07-20
forum: Installation &amp; Upgrades
---

### Post by tsara on 2017-07-20
HI,
I'im very glad to write here with some sentence my problem about on my HP probook 6450b with UBUNTU 16.04,
I'have converted the HDD MBR TO GPT, and it's ok ! I used boot from usb live EFI and i activate the UEFI in my firmware HP. So, i've create a partition /boot/efi vfat with GPARTED, and then i have to be continued the installation with other both swap /, /home.... when the installation is completed  and rebooting, after the LOGO's HP is displaying, the boot is not good, black screen and check cable etc.... so, i tryed to boot with usb uefi live , the boot is good, so, i'm looking at the DISK USB BOOT and i have copy the path /EFI/BOOT on the DISK USB and i paste it in my partition /boot/efi/EFI

$ cp -r /cdrom/liveusb/EFI /boot/efi/

with this parts, my OS ubuntu booting but
these sentences flash in preboot

error: file '/boot/' not found
error: No such device: /.disk/Info 
error: no such device /.disk/mini-info

What's are these sentence
I'm sorry for my bad speaking

---

### Post by oldfred on 2017-07-20
The version of grub boot files on the flash drive are configured only for booting the flash drive. It is a minimal grub.
You should be able to use Boot-Repair to install the UEFI version of grub correctly to your ESP - efi system partition.

First lets see your configuration.
 Just run the summary report, the auto fix sometimes can create more issues.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

If you do reinstall grub before someone reviews your install, only use the advanced mode and select your install.

Also HP has not been UEFI dual boot friendly.
      
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[URL="http://ubuntuforums.org/showthread.php?t=2131886"]http://ubuntuforums.org/showthread.php?t=2131886
[/URL]
 escape + F9 for boot menu, F10 for bios setup
[http://askubuntu.com/questions/870453/live-boot-usb-install-of-16-04-fails-on-hp-pavilion-23?noredirect=1#comment1349777_870453](http://askubuntu.com/questions/870453/live-boot-usb-install-of-16-04-fails-on-hp-pavilion-23?noredirect=1#comment1349777_870453)
[http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook](http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook) 

[URL="http://ubuntuforums.org/showthread.php?t=2131886"]
[/URL]

---

