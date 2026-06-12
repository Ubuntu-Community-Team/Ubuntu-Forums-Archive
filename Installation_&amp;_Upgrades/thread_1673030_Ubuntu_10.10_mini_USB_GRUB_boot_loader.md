---
title: "Ubuntu 10.10 mini USB GRUB boot loader"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by Alxl on 2011-01-21
I have installed Ubuntu 10.10 Minimal on a 2GB USB using CLI and it is working very well after I added a few things. I intend to use it on machines other than my own. But the GRUB boot loader was installed to the main system on my machine and it is booting from there.
    
    During the installation it was said that the bootloader can be installed on a floppy. So I started a new 2 GB stick and tried to install the boot loader on a floppy but my computer does not recognize floppies anymore (seems to be a wider problem with recent distributions).

    So I tried to install the bootloader on a different USB stick and and this also did not work.
    
    Cannot find recent and **relatively easy** way to install GRUB boot loader to a stick.
        [LEFT]Any help appreciated[/LEFT]

---

### Post by oldfred on 2011-01-21
You just install grub to the root partition of whatever drive the USB mounts as:

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

You will have to manually add entries to grub.cfg. They can be standard boot enties, even one's you copy from your standard install or loop mount ISO's:

ISO Booting with Grub 2 - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)

---

### Post by Alxl on 2011-01-23
[FONT=Georgia][FONT=Courier]Thanks [/FONT]oldfred,[/FONT]    [LEFT][FONT=Georgia][FONT=Courier]I did follow the instructions and installed GRUB2  and   grub.cfg  to a stick.[/FONT][/FONT][/LEFT]
    [LEFT][FONT=Georgia][FONT=Courier]This sticks allows me to go to BIOS on my machine , click on USB and it automatically boots to my main machine (does not allow to start the other USB). I believe that I can follow instructions and make it first to boot all the time,  yet only on my machine.[/FONT][/FONT]
[FONT=Georgia][FONT=Courier]
[/FONT][/FONT][/LEFT]
        [LEFT][FONT=Georgia][FONT=Courier]But what I need is for the Grub stick to be first to boot on any machine and to give me the option to start Ubuntu on the other stick.
[/FONT][/FONT]
[FONT=Georgia][FONT=Courier]Here is what I got so far [/FONT][FONT=Courier]on my /media/GRUB2/:                                                                                                                      $ sudo grub-mkconfig -o /media/GRUB2/boot/grub/grub.cfg    gives me: [/FONT][/FONT][/LEFT]
    [LEFT][FONT=Georgia][FONT=Courier]'Generating grub.cfg ...[/FONT][/FONT][/LEFT]
    [LEFT][FONT=Georgia][FONT=Courier]Found linux image: /boot/vmlinuz-2.6.32-27-generic[/FONT][/FONT][/LEFT]
    [LEFT][FONT=Georgia][FONT=Courier]Found initrd image: /boot/initrd.img-2.6.32-27-generic[/FONT][/FONT][/LEFT]
    [LEFT][FONT=Georgia][FONT=Courier]Found memtest86+ image: /boot/memtest86+.bin[/FONT][/FONT][/LEFT]
    [LEFT][FONT=Georgia][FONT=Courier]done&#8217;

[/FONT][/FONT][/LEFT]
        [LEFT][FONT=Georgia][FONT=Courier]How do I make it to be the first to boot on _[COLOR=Black]any machine[/COLOR]_ (without having to go to the BIOS)   and then let me chose the Ubuntu distribution on the other USB?[/FONT][/FONT]
[FONT=Georgia][FONT=Courier]Thanks
[/FONT][/FONT][/LEFT]
   
  [FONT=Georgia]
[/FONT]

---

### Post by oldfred on 2011-01-23
BIOS controls booting. You cannot make a system boot from another drive than what is set in BIOS. So I do not think it is possible to do what you want.

---

