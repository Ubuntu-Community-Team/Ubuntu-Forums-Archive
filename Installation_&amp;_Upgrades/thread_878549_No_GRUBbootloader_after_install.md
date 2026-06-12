---
title: "No GRUB/bootloader after install"
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by afbuk2008 on 2008-08-03
CPU Type	        DualCore Intel Core 2 Duo E8400, 3000 MHz 
Motherboard Name	Asus Maximus Formula  
Motherboard Chipset	Intel Beachwood X38
System Memory	        4096 MB
Video Adapter	        NVIDIA GeForce 8800 GTS 512
Disk Drive	        500 GB, 7200 RPM, SATA-II) x 2

I installed the latest version of Ubuntu installation all went 'fine', up until i rebooted. When i was asked to take the cd out of the drive, then press enter, i did. PC restarted then it just loaded vista, no boot loader, no grub, nothing. 
Every time i restart or turn the pc on it doesn't give me an option to load ubuntu.

Can anyone help me out please :(

---

### Post by Vakman on 2008-08-03
Have you tried using "Super GRUB Disk" ([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)) it always bails me out. First thing I go with when this kind of thing happens. What I am finding interesting though is that it loaded Vista. Usually when I hear this it would load into Ubuntu and not allow you to load into Vista.

---

### Post by Sef on 2008-08-03
> Thisislaw  	
Re: No GRUB/bootloader after install
Have you tried using "Super GRUB Disk" ([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)) it always bails me out. First thing I go with when this kind of thing happens. What I am finding interesting though is that it loaded Vista. Usually when I hear this it would load into Ubuntu and not allow you to load into Vista.
1

+1.  Super GRUB Disk is easy to use.

---

### Post by afbuk2008 on 2008-08-07
I have tried the supergrub disk and it seems unsucessful.
I can either get it so that grub is the bootloader and gives me the option to boot ubuntu and vista... however when i choose the vista option it says that there is no master boot record and i have to press ctrl+alt+del to restart.

I am able to access ubuntu but not vista in that state.

Can anyone help? 

Thanks so far guys/girls

---

### Post by adrian15 on 2008-08-22
> **afbuk2008 said:**
> choose the vista option it says that there is no master boot record 

If you choose **!Windows!** at the first menu, does Vista boot ok?

adrian15

---

