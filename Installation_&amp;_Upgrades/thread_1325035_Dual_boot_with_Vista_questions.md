---
title: "Dual boot with Vista: questions"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by bhanja_Trinanjan on 2009-11-13
[FONT="Arial"][SIZE="3"]Hi,
	I decided to try out UBUNTU 9.10. I have one 500GB drive and a 320 GB one.

Vista is installed on the 500GB drive.
As my motherboard supports the selection of a boot drive, I decided to install Linux on the 320GB one. 
I wanted to handle dual boot with the BIOS and not GRUB.
So I disabled the 500GB drive from the BIOS and proceeded with the installation.

Although the 1st HDD is disabled, the UBUNTU installer still sees that drive! However, the 500GB drive is indeed disabled as booting shows the ‘INVALID BOOT DISK’ error.

Given the circumstances that I cannot disable the 500GB Vista HDD and do not wish to take the trouble of disconnecting it, how do I proceed?

The installer gives me the option to use the 320GB HDD entirely… but does that affect the Vista MBR on the 500GB Vista drive? 
What happens when GRUB is installed in this scenario? 

Because, I do not want to have Vista as an option in GRUB, I just want to make that selection via the BIOS.

Please help!
[/SIZE][/FONT]

---

### Post by ShadowMage on 2009-11-13
If you don't want GRUB, you can tell the Ubuntu installation not to install it. On the last step of the Ubuntu 9.10 installation, but *before* you finalize and hit Install, click on the "Advanced..." button. In there, you can uncheck "Install boot loader". But since I've always used GRUB, I'm not sure how this would work out if you don't have any bootloader.. However, in there, you can also (keep "Install boot loader" checked and) select where to install GRUB. So I would imagine you just need to make sure not to install it on your Vista drive.

Unfortunately, I have one HD, and I use GRUB to select my OS, so I can't test or verify these.

---

### Post by davidryderuk on 2009-11-13
Hi,
There is a link below which tells you how to install grub specifically onto the ubuntu partition. 

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

You only need to read "The Ubuntu Side of Things" since your motherboard will hopefully do the same job as easybcd.

---

### Post by oldfred on 2009-11-13
If you are going to use the BIOS to switch drives to boot you still need Grub in the MBR of the Ubuntu drive. You keep the Windows boot in the Windows drive and BIOS causes the boot from whichever MBR is the first drive.
You install Grub to the partition if you are chainbooting from one sytem into another. That is how Grub actually boots windows as part of the windows boot is also in the windows partition. The Windows boot in the MBR only jumps to the windows partition boot, just like grub does.

Just make sure what drive is first by the installer and use the advance tab to install Grub to your Ubuntu drive.

---

### Post by bhanja_Trinanjan on 2009-11-14
Thanks! Solved... set GRUB to install to the Ubuntu drive.

---

