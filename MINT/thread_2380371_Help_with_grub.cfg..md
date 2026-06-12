---
title: "Help with grub.cfg."
date: 2017-12-16
forum: MINT
---

### Post by kabbjolf on 2017-12-16
Dear forum.
I decided to return to linux after 8 years and installed mint 18.03. Unfortunately the installer always crashed upon installing grub, all 5 times i tried. 
Luckily the android-x86 grub installer works perfect but the android-x86 was not able recognizing the mint install, only the win 10 partition and android-x86. Easiest now would be to just add the ubuntu partition in the grub.cfg android-x86 setup for me but i need help with boot script how to crank ubuntu (kernel and initrd.img). I know where its located on my harddrive, i just need the specific ubuntu start procedure to copy into my working android-x86 grub setup, any tips for boot toram is appreciated.

I tried posting my questions in the linux mint forum but my question was refused for some reason.

Kindly Knabbjolf.

---

### Post by oldos2er on 2017-12-16
Thread moved to *MINT*

---

### Post by oldfred on 2017-12-16
Are both/all installs UEFI or all BIOS boot mode?
If not you cannot dual boot from grub as UEFI & BIOS are not compatible. You then can only dual boot from UEFI boot menu.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by kabbjolf on 2017-12-16
It is uefi but to my surprise syntax is almost same as with grub1 syntax so it was easy for me catching up.

System is working dual boot thanks to android-x86 installer, i just want to add the ubuntu installation as ubuntu installer failed installing grub. If i get a sample of syntax from someones working grub.cfg the problem is solved as I will easy map the local partitions I have installed, I just need the cheat codes starting ubuntu specifically as all other systems as win 10, puppy linux android-x86 is working perfect, its just ubuntu that fails.

---

### Post by oldfred on 2017-12-16
Without knowing details cannot make specific suggestions:

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by yancek on 2017-12-16
I don't use any Android but you see to be saying it uses Grub2.  If that's the case, why don't you just run the grub-mkconfig command from the Android to add a menuentry for Mint?

---

### Post by virgosun on 2017-12-17
Just copy rEFInd to your ESP/EFI, it will detect linux kernel and let you boot to Mint

I have androidx86 but I load it by Ubuntu's grub instead of it own grub
So I don't know how the androidx86 grub.cfg look like
But this entry is from Kali iso grub.cfg
```

menuentry "Live system (persistence, check kali.org/prst)" {
    linux /live/vmlinuz2 boot=live components splash username=root hostname=kali persistence
    initrd /live/initrd2.img
}

```
In your system I think you just need to add 
```

set root=(hdX,gptY)

```

---

### Post by kabbjolf on 2017-12-17
If someone ends up in same dilemma here is a copy of a working grub.cfg. To find uuid of the install run "sudo blkid".

Admin, remove the alias "kabbjolf" out of my profile as it is misspelled and im highly miscontempt Im not allowed editing my personal details myself.
-----------------------------------------------------------------------------

set timeout=2


menuentry "Android-x86 6.0-r3" {
    search --set=root --file /android-6.0-r3/kernel
    linux /android-6.0-r3/kernel quiet root=/dev/ram0  
    initrd /android-6.0-r3/initrd.img
}
menuentry "Android-x86 6.0-r3 (DEBUG mode)" {
    search --set=root --file /android-6.0-r3/kernel
    linux /android-6.0-r3/kernel root=/dev/ram0  DEBUG=2
    initrd /android-6.0-r3/initrd.img
}
menuentry "UrButNu" {
    set root=(hd0,7) 
    search --no-floppy --fs-uuid --set=root c8d502e1-30a0-4d58-9bb5-5ca70f51e2e4
    linux /vmlinuz root=UUID=c8d502e1-30a0-4d58-9bb5-5ca70f51e2e4 ro nosplash toram
    initrd /initrd.img 
}

---

