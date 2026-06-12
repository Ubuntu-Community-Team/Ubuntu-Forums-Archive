---
title: "No grub menu after ubuntu install"
date: 2013-08-31
forum: Installation &amp; Upgrades
---

### Post by renu2 on 2013-08-31
Hi all,

I have installed ubuntu alongside Windows 8 on a HP laptop. Restarting after install, the machine went straight to Windows. I also ran boot-repair which did not help. boot-repair did not report any errors. There is still no grub menu. Boot info created after running boot-repair is at [http://paste.ubuntu.com/6048540/](http://paste.ubuntu.com/6048540/). 

Any suggestions?

Thanks
Renu

---

### Post by oldfred on 2013-08-31
Welcome to the forums.

I do not see anything really wrong.
Try going into UEFI/BIOS menu and choose the ubuntu entry. It should then boot Ubuntu. And if that works you may have to change a setting to make it the default. And Windows repairs may reset defaults, so if that happens you have to go in and change it again.

Grub2 has a bug and does not create correct boot entries. But Boot-Repair goes in and creates correct boot entries for all the efi files it finds. But then with HP, it has an efi folder with many efi files. You may not need all those entries and can at least for now remove the os-prober entries. Details in cleaning up grub menu are in link in my signature.

---

### Post by renu2 on 2013-08-31
Thank you for the quick response. I did not know about UEFI menu. I found it and after choosing Ubuntu I could see grub menu. I could still boot into only recovery mode possibly because of video drivers which is a different issue.

Which setting do I need to change to see grub menu without going through UEFI BIOS menu?

Thanks
Renu

---

### Post by oldfred on 2013-08-31
Just like with BIOS where you set default boot order, you should have a setting on first, second etc boot order. Set Ubuntu as first.
You also should have a one time boot key often f12 to choose to boot another entry. Best to use for booting DVD or USB flash drive.
If secure boot is on, only devices seen as secure boot will be shown.

Recovery mode has nomodeset as default. You can use e on grub menu, scroll to linux line and replace quiet splash with nomodeset. And if you have nVidia or AMD you proably need the proprietary drivers. If dual video check into bumblebee. More info in link in my signature.

---

### Post by renu2 on 2013-08-31
I did not find a way to edit the options in the boot menu. In BIOS menu reached with F10 I could change the order of devices. But Ubuntu was not listed there. I saw a related thread at [http://askubuntu.com/questions/327676/dual-boot-menu-with-ubuntu-and-windows-8-not-showing-up](http://askubuntu.com/questions/327676/dual-boot-menu-with-ubuntu-and-windows-8-not-showing-up). After running boot-repair again with the option "Boot-Repair[COLOR=#333333][FONT=UbuntuRegular] --> [/FONT][/COLOR]Advanced Options[COLOR=#333333][FONT=UbuntuRegular] --> tick the [/FONT][/COLOR]Backup and rename the Windows EFI files[COLOR=#333333][FONT=UbuntuRegular] option" grub menu became available immediately on machine start up. 

I will look up on nVidia drivers and removing additional boot options available.

Thanks again for quick help.
Renu

[/FONT][/COLOR]

---

