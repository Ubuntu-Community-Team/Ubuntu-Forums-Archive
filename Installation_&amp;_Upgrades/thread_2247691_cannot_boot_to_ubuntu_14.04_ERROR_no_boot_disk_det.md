---
title: "cannot boot to ubuntu 14.04 ERROR: no boot disk detected."
date: 2014-10-09
forum: Installation &amp; Upgrades
---

### Post by Gerardo_Ochoa on 2014-10-09
Hello, i just bought a desktop pc that came with windows 8.01 originally. the goal is to run ubuntu 14.04 by itself so I downloaded it and installed it. however, ubuntu is not loading, it keeps getting an error message saying "Error: no book disk was detected". Note: i do NOT want to run windows on this pc but ubuntu by itself.  any help would be greatly appreciated. when I look on the UEFI menu, i can see under boot order that ubuntu is an option but even if i make it number 1 on the boot order list it does not boot.  I am able to boot to the ubuntu  DVD, i tried running boot-repair but it did not work either.

---

### Post by Vladlenin5000 on 2014-10-09
Hi, welcome.

This is what you need to read, understand and install accordingly (you can skip the parts regarding dual-boot scenarios): [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by yancek on 2014-10-09
>  i tried running boot-repair but it did not work either. 		

Boot repair has an option which will output a text file with info on your drives, partitions and boot files along with other information.  Try running it again and posting that here.

---

### Post by oldfred on 2014-10-09
Besides summary report as suggested by yancek, what brand, & model system it this? Also what video card?

Some require work arounds as they only want to boot Windows.

---

### Post by Gerardo_Ochoa on 2014-10-19
just wanted to let everyone know I am closing this thread. found my solution on this website. [http://ubuntuforums.org/showthread.php?t=2238714](http://ubuntuforums.org/showthread.php?t=2238714)

[COLOR=#ff0000]HP and Sony only boot Windows. So we have many work arounds, some work better than others.

Since you do not have any Windows you can just create the Windows efi boot file with the Windows name. Then the UEFI will think it is booting Windows but really boots grub.

You will have to recreate in the efi partition the Windows folder, a boot folder under Windows and copy grubx64.efi into that folder and rename it to bootmfgw.efi.

mount /dev/sda1 /mnt
cd /mnt/EFI

use ls to see if mounted correctly
ls -l
mkdir Microsoft
mkdir Microsoft/Boot
cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Microsoft/Boot/bootmfgw.efi 

Most systems also have a /Boot folder and can boot grub from that using a hard drive entry.
mkdir Boot

cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Boot/bootx64.efi

Your ls -l should then have this in the efi partition:

/EFI/Boot
/EFI/Microsoft/Boot
/EFI/ubuntu[/COLOR][COLOR=#ff0000][/COLOR]

---

