---
title: "Can't Install Ubuntu"
date: 2018-01-03
forum: Installation &amp; Upgrades
---

### Post by idea2form on 2018-01-03
[FONT=arial]Here are the steps I have taken. 
[LIST]
[*]Downloaded .iso
[*]Used Rufus to make bootable usb drive
[*]Installed Ubuntu 14.04 on my Laptop with drive.  Works great!
[*]On my big PC I see this screen (not my screenshot)  [https://drive.google.com/file/d/1ZXikcGxIjhoBCADKLPYQOajT7BsVQvq6/view](https://drive.google.com/file/d/1ZXikcGxIjhoBCADKLPYQOajT7BsVQvq6/view)
[*]When I try to install ubuntu the same way as my Laptop I get this error (my screenshot) [https://photos.app.goo.gl/A5vYLwU5ChGq8U7J3](https://photos.app.goo.gl/A5vYLwU5ChGq8U7J3)
[/LIST]

After this error my entire PC is frozen.  I can not use the keyboard at all.  From here I can hold in the power button until my PC restarts and then choose the hard-drive with Windows on it.  That loads up.

[LIST]
[*]I researched the error and performed Microchip update from the windows side.  I followed the following video on updating the microcode from the windows. It was successful so I assume I now have the latest from Intel. [https://www.youtube.com/watch?v=nEYqw5tvZHs](https://www.youtube.com/watch?v=nEYqw5tvZHs)
[*]I asked Reddit what to do.
[*]Reddit said "I get this error since I updated the kernel to 4.13. It's due to the missing intel ucode, which is just a warning and nothing else. Also just installing it, doesn't automatically resolve the 'error', you have to add intel-ucode image to the bootloader you are using."
[/LIST]

I have no idea how to do this. 
[/FONT][COLOR=#333333][FONT=Ubuntu]From my research there is a file /boot/loader/entries/entry.conf that needs the image as the third initrd as follows.
[/FONT][/COLOR]title   Arch Linux
linux   /vmlinuz-linux
initrd  /intel-ucode.img
initrd  /initramfs-linux.img
options ...

[FONT=arial]I have no clue where this file is that needs the modification (my usb stick???)
I have no clue how to install "intel ucode.  Searches on this give me results that are hard to follow.
Articles like this scare me. [https://wiki.archlinux.org/index.php/microcode](https://wiki.archlinux.org/index.php/microcode) 
I need a little more step by step.  This is my first day with Linux in my life. 
[/FONT]

---

### Post by Frogs Hair on 2018-01-03
Moved to*** Installations & Upgrades***

---

### Post by idea2form on 2018-01-06
I updated my bios now it looks like this [https://drive.google.com/open?id=0B2rMFtp__ys_QnhaamI0V0dybVU3a0lnRERPM05LMEtoc2pj](https://drive.google.com/open?id=0B2rMFtp__ys_QnhaamI0V0dybVU3a0lnRERPM05LMEtoc2pj)

---

### Post by RobGoss on 2018-01-06
Please provide the specs for your machine it will help to determine what might be the problem

---

### Post by grahammechanical on 2018-01-06
Silly question time. Does Ubuntu load? At the top of the page I see "please update microcode to version 0x22 (or later). If Ubuntu loads it might be possible to install a CPU microcode driver. System Settings>Software & Updates>Additional drivers.

I have never updated my BIOS but the motherboard user guide has instructions that include backing up the BIOS and restoring the original BIOS. Your motherboard BIOS setup utility may have similar functions. Or check the instructions for the utility that upgraded the BIOS.

If Ubuntu loads to an unusable state, then, at the grub boot menu select Advance options for Ubuntu and at the recovery menu select resume. That will attempt to load Ubuntu with a low resolution video driver. which may get you to a working desktop

Regards.

---

