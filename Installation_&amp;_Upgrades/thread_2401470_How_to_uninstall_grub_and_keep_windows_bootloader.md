---
title: "How to uninstall grub and keep windows bootloader?"
date: 2018-09-18
forum: Installation &amp; Upgrades
---

### Post by grandkodiak2 on 2018-09-18
Hello,

I have installed many different types of linux flavors over the years, but I'm stumped because this is the first time I've ever tried to REMOVE one lol. Usually I just delete partitions and reinstall new versions or what have you, but I have an old laptop thats dual win10 and ubunutu that I need to give back wholly to windows. If I delete the swap/root/user partitions I'm guessing it'll still boot to grub with the list options, where I'd like to have it where it just goes back to windows auto loading as the sole boot loader without having to reinstall windows.

thanks!

---

### Post by oldfred on 2018-09-18
UEFI or BIOS?

If BIOS, just be sure to install Windows boot loader to MBR first before deleting partitions, or system will not boot as only part of grub is in MBR, and then that part will not find the rest of grub.

If UEFI, be sure to go into UEFI and set Windows as first in UEFI boot order.
You also can delete the UEFI boot entries that say ubuntu and the /EFI/ubuntu folder in the ESP - efi system partition. If you ran Boot-Repair and it converted /EFI/Boot/bootx64.efi to a copy of shimx64.efi, change it back to a copy of Windows .efi boot loader.

       Uninstall Ubuntu from menu, Really UEFI boot menu 
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi)

---

### Post by scubadoo on 2019-07-14
For UEFI and if you can boot into Windows:

(If the issue is just that you need to remove grub (but you didn&#8217;t delete the Windows boot loader), then you can do that without any installation media.)

Open the command prompt as an Administrator (e.g. press the Win key then search &#8216;command prompt&#8217;; right click and select &#8216;Run as administrator&#8217;)
Mount the EFI partition where the boot loaders are stored by running mountvol z: /s (you can use any letter if z is taken)
Move to this partition by typing z: and Enter
Move to the folder with the boot loaders by running cd EFI
Remove the ubuntu boot loader by running rmdir ubuntu and accept default Y (recursive)
Run dir to check what other bootloaders you have. There should a be Microsoft one and there might be a Boot one.
Exit console and reboot.

---

