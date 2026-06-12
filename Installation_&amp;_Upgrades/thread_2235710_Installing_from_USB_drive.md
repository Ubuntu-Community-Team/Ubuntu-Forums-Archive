---
title: "Installing from USB drive"
date: 2014-07-22
forum: Installation &amp; Upgrades
---

### Post by Mariano_Belgrano on 2014-07-22
Hello

I have 2 computers and I cannot get Ubuntu started in both of them.

I have taken a picture of the screen where it freezes and CAPS LOCK kept flashing.

My computers are:

1) Desktop computer P5N-E SLI mobo  / the picture attached is from this computer
2) Samsung laptop Series 5 model NP510R5E-A02UB

Thanks for your help!

Mariano

---

### Post by Mariano_Belgrano on 2014-07-22
Sorry the image was too small. Here I send a normal size picture.

---

### Post by Mariano_Belgrano on 2014-07-22
Sorry about the orientation of the picture but in photoshop and windows picture viewer the orientation display came out correctly.

---

### Post by oldfred on 2014-07-22
What video card and processor?
If older it may not be able to handle full Ubuntu with Unity. My old laptop has Ubuntu but Unity just will not run, so I install fallback.
With my desktop I can run Unity but prefer fallback. But I have nVidia 9600GT and on every boot until I get nVidia driver installed I have to add nomodeset boot parameter. Other computers may need different boot parameters.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.

Is Samsung also UEFI? That would install significantly differently.
      
 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

Other Samsungs, may be similar. Newer 14.04 should install easier.

 How to: Dual boot Windows 8 and Ubuntu 13.10 on Samsung 900X3E 
[http://ubuntuforums.org/showthread.php?t=2176559](http://ubuntuforums.org/showthread.php?t=2176559)
Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)
Samsung series 5 UltraBook, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)

---

