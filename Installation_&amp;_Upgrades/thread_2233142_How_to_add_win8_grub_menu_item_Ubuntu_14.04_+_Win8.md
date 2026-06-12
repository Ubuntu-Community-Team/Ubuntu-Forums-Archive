---
title: "How to add win8 grub menu item: Ubuntu 14.04 + Win8 UEFI dual boot"
date: 2014-07-06
forum: Installation &amp; Upgrades
---

### Post by Paul_Bouchier on 2014-07-06
Hi,

I have a 2013 HP Envy dv7 with Win8 pre-installed, upgraded to Win8.1. I shrank the windows partition by 100MB and made two new partitions for Ubuntu (root + home - 80MB on /dev/sda7, swap - 20MB on /dev/sda8). I basically followed these instructions:
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html) 
including the boot-repair steps on linux and Windows. Secure boot is disabled. After that it would always boot into windows, except if I pressed Esc then F9 for a one-time boot into Ubuntu. Progress.

The problem with always booting into Windows turned out to be that HP UEFI ignores the boot path if it finds a bootable efi file in either of two locations and always runs them if they exist, and they boot into Windows. That problem is described here:
[http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and-Software/Changing-Boot-Order-on-Dual-Boot-Windows-8-and-Ubuntu/td-p/2503733](http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and-Software/Changing-Boot-Order-on-Dual-Boot-Windows-8-and-Ubuntu/td-p/2503733)

I followed the suggestion in that thread and renamed the two windows efi files, and ran efibootmgr and set the boot path to Ubuntu, and now it boots happily into Ubuntu, but I can't boot into Win8 except by pressing Esc then F9 then selecting boot from EFI file and navigating the EFI filesystem down to the (renamed) windows efi boot files. Progress. Apparently Win8 and Ubuntu are happy co-existing in different partitions, and I haven't destroyed either of their boot loaders. However, the method of booting windoze is unsatisfactory. I've tried unsuccessfully to add a Win8 boot entry to grub, and am hoping for a pointer to make that part of it work.

I tried boot-repair twice after installing Ubuntu, without success. (This was prior to renaming the two efi files).The second time I used the advanced option as described elsewhere in this forum to work around the hard-coded boot path  It didn't work, and the second run left me with a system that would only boot windows, and I had to reinstall Linux from the thumbdrive, so I'm a bit gun-shy about boot-repair. The paste files are: [http://past.ubuntu.com/7754927](http://past.ubuntu.com/7754927) and 7755416 in case it's description of my config is useful.

I added the following entry to /etc/grub.d/40_custom in an attempt to get windows to boot from the grub boot menu:
menuentry "Windows 8" {
insmod part_gpt
insmod fat
insmod search_fs_uuid
insmod chain
search --fs-uuid --no-floppy --set=root 6CF9-6F76
chainloader (${root})/efi/Boot/bootx64Win8.efi
}
I ran update-grub, and the new menu item shows up, but when I select it it gives an error saying unable to load that efi file. (It's finding the file, because before I got the UUID right it would say it couldn't find the file.)

I'm pretty far out of my depth by now, and would appreciate any pointers for getting Windoze to boot from the grub menu. The grub menu says it's version 2.02, which should be what came off the Ubuntu install.

Thanks in advance for any suggestions

Paul

---

### Post by oldfred on 2014-07-09
Did you change the name of the Windows efi file to /efi/Boot/bootx64Win8.efi? It is normally /efi/Microsoft/Boot/bootmgfw.efi? 

Also grub only boots Windows 8.1 from grub menu if secure boot is off.

Normally users are able to rename shim.

 Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry.

[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

---

