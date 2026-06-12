---
title: "Search for bootable 12.10 distro"
date: 2013-03-11
forum: Installation &amp; Upgrades
---

### Post by dgundling on 2013-03-11
Does anyone know where I might be able to obtain a bootable version of Ubuntu 12.10? I now have 4 different distros of 12.10. two are from Ubuntu User magazine, one is from Linux user magazine, and the last one was obtained from the Ubuntu download center. I can get to the point where the sreen message is "installation has finished need to restart. Upon restart I get the grub menu. When ubuntu 12.10 is selected I get to the log in screen, log in, and then I either get the frozen coloored screen or I get "compiz has enexpectadly closed". Did get an error message saying that some of the installed packages were obsolete and requesting that I install updated packages. How one does that install when the OS isn't functional is a bit puzzling.

---

### Post by plucky on 2013-03-12
> **dgundling said:**
> Does anyone know where I might be able to obtain a bootable version of Ubuntu 12.10? I now have 4 different distros of 12.10. two are from Ubuntu User magazine, one is from Linux user magazine, and the last one was obtained from the Ubuntu download center. I can get to the point where the sreen message is "installation has finished need to restart. Upon restart I get the grub menu. When ubuntu 12.10 is selected I get to the log in screen, log in, and then I either get the frozen coloored screen or I get "compiz has enexpectadly closed". Did get an error message saying that some of the installed packages were obsolete and requesting that I install updated packages. How one does that install when the OS isn't functional is a bit puzzling.

What are the specifications of your hardware?

This sounds as though you don't have the required hardware to run Compiz.

Ubuntu 12.10 is the first release that doesn't have Ubuntu 2D included, and so will not run on any system that will not support Compiz.

If your hardware is good enough,try adding **nomodeset** to the boot menu in Grub.


Good Luck

---

### Post by dgundling on 2013-03-13
> **plucky said:**
> What are the specifications of your hardware?

This sounds as though you don't have the required hardware to run Compiz.

Ubuntu 12.10 is the first release that doesn't have Ubuntu 2D included, and so will not run on any system that will not support Compiz.

If your hardware is good enough,try adding **nomodeset** to the boot menu in Grub.


Good Luck
   Thanks for the reply  

In response to what you said, I checked the system requirements for 12.10. They looked pretty benign and my system meets them. 

Being new at UBUNTU, how do I go about putting nomodset in the grub boot menu?  BTW, I have a multiboot (11.10, 12.04, and 12.10) ( 12.10 is not working)

---

### Post by plucky on 2013-03-13
> Being new at UBUNTU, how do I go about putting nomodset in the grub boot menu? 

At the grub menu, select 12.10 and then type e.

This will take you to the edit menu.

You should see > menuentry 'Ubuntu, with Linux 3.8.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root fa45b1dd-d6c0-49ff-877e-bc05f220a054
	linux	/boot/vmlinuz-3.8.0-12-generic root=UUID=fa45b1dd-d6c0-49ff-877e-bc05f220a054 ro   quiet splash **nomodeset** $vt_handoff
	initrd	/boot/initrd.img-3.8.0-12-generic


Put nomodeset after "quiet and spash" and then press F10 to continue booting.

This change is not permanent and will last for only one boot.

If you want it to be permanent,you have to edit the file /etc/default/grub and put nomodeset

in this line > GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

then run update-grub

Good Luck

p.s. My test system has run from Edgy to Precise but could not handle compiz and 12.10 was glacial slow.

---

### Post by dgundling on 2013-03-19
As stated earlier, I have two computers on which I am trying to run 12.10. Tried the suggested *nomodeset* approach without success on the older of the two (Intel Pentium 2.4 GHz with 2GB of memory using the Mobo on board video) . Went to try it on the newer of the two (AMD 3.4 GHz, 2GB and a separate video card) and on boot up it worked. Ihad changed nothing from the last time I tried to run 12.10. The last time I tried to run it it hung on the purple splash screen. Any further ideas of what I might try to get past the splash screen which follows the log in page? Thanks for your help.

---

