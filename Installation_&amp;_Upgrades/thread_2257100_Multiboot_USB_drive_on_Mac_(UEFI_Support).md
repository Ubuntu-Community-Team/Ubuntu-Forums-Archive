---
title: "Multiboot USB drive on Mac (UEFI Support)?"
date: 2014-12-16
forum: Installation &amp; Upgrades
---

### Post by Zythyr on 2014-12-16
Until now I have been using YUMI in which I loaded multiple operating systems (Windows 7, 8, Ubuntu, Mint)  for easy on the go installing/live USB. I never had issue with a Windows based laptop or desktop. 

I just got a Macbook Pro. I was trying to install Windows and Ubuntu but had a luck loading the USB. Mac's boot sequence wouldn't detect the USB. After digging around I read something about only EFI/UEFI being supported on Mac because it doesn't have a BIOS. 

How can I create a multiboot USB that will allow me to install Windows and Ubuntu onto the Mac or any other laptop that doesn't support the legacy (BIOS) based booting method?

---

### Post by oldfred on 2014-12-17
I have no idea if it works on a Mac, but I did create one on my new UEFI system. So far I only copied one ISO into my FAT32 partition (gparted), but plan on adding another partition for many ISO. I did keep my efi partition too small for many ISO.

       Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/](http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/)
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi)

    Some more Mac specific commands:
[http://ubuntuforums.org/showthread.php?t=2051337](http://ubuntuforums.org/showthread.php?t=2051337)

I just created a gpt partitioned drive with gparted, created an efi partition, FAT32 formatted with boot flag in gparted.
I then created folders
drwx------ 3 fred fred 4096 Nov 29 15:22 boot
drwx------ 4 fred fred 4096 Nov 29 13:53 EFI
drwx------ 2 fred fred 4096 Dec  7 15:46 iso

I copied my grubx64.efi & shimx64.efi from my Ubuntu efi folder in my working system to an EFI/Boot folder on flash drive. I then manually created a grub.cfg. I also copied fonts folder & modules folder into /boot/grub as those are expected.
When copying files like this the preconfigured grubx64.efi has specific requirements on paths and files in efi partition. 
Probably correct way is to use grub-mkimage where you tell it paths, and many settings.    

This was the grub I put into the /efi/boot folder but it does not seem to be used.
```
insmod part_gpt
insmod fat
set root='hd0,msdos1'
menuentry 'Live ISOs' {
configfile (hd0,1)/iso/livecdimage.cfg
} 

```

This was the grub I put into /boot/grub and was the one that came up.
```
# grub.cfg 
set default=0 
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
set gfxpayload=800x600


menuentry " " {
set root= 
}

menuentry 'Live ISOs' {
configfile (hd0,1)/iso/livecdimage.cfg
} 

menuentry " " {
set root= 
}

menuentry "Reboot" {
    reboot
}

menuentry "Halt" {
    halt
}

```


I like to have a text file that grub calls, so I do not edit grub, but edit text file. In this case it does not really matter, but when in my working installs I can change ISO without having to run sudo update-grub.

In my iso folder I have this and all the ISO. (Will change to another partition later.
```
# livecdimage.cfg
# Add this to 40_custom to load this file:
# menuentry 'Live ISOs' {
# configfile (hd2,4)/iso/livecdimage.cfg
#} 
# Add iso names to livecdimage.cfg
#for i in `ls *.iso`;do echo "# "$i>>livecdimage.cfg; done;


menuentry "gparted (Boot ISO Image via Grub2) " {
    insmod part_gpt
    set isofile="/iso/gparted-live-0.19.1-1-amd64.iso"
    loopback loop (hd0,1)$isofile
#    linux (loop)/live/vmlinuz live-media=iso=$isofile keyb=us gl_kbd=us gl_lang=en_US gl_numlk=off gl_batch boot=live union=aufs  #toram=filesystem.squashfs noswap noprompt vga=791
#        linux (loop)/live/vmlinuz fromiso=$isofile boot=live noswap
        linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt ip=frommedia findiso=$isofile toram=filesystem.squashfs
    initrd (loop)/live/initrd.img
}
# linux /workdir/vmlinuz fromiso=/dev/sda11/debian-live-6.0.3-i386-lxde-desktop.iso boot=live config BOOT_IMAGE=/live/vmlinuz


```

 This will boot an ISO from a hard drive or any second drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

---

