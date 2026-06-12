---
title: "Installation won't complete, computer won't boot"
date: 2015-10-07
forum: MINT
---

### Post by ogp on 2015-10-07
Hello, 

I am having problems installing Linux Mint on an old laptop. The machine is a Compaq Evo N1015v (more than 10 years old), and the BIOS won't allow it to boot from a USB stick. However I can use Plop Boot Manager on a CD to then boot from a bootable USB stick, and a live session runs well (although a little slowly). 

Installing from the live session seems to go normally, but the installation never completes; the installation window goes away but the normal cursor never comes back - it shows the spinning 'Please Wait' cursor and stops there. The computer seems to carry on working fine (it doesn't freeze up), but nothing more happens. If I use gparted to look at the partition I have installed into then it tells me that there is a Mint installation on there. I am therefore guessing (although it's only a guess) that the installation happens but the installer is unable to set the boot process correctly. 

If you close the machine down (end the live session) and reboot, the machine shows the message "Operating system not found". If I boot back into another live session (from Plop Boot Manager and a USB stick) and install Yannubuntu's Boot-Repair then it is unable to repair the boot and gives me the message "Please enable a repository containing the [linux-generic] packages in the software sources of Linux (sda1). Then try again". The BootInfo Summary it creates is here: 

[http://paste2.org/N7szWtFd](http://paste2.org/N7szWtFd)

If anyone can give me any help with this then I would be very grateful - thank you. 


Oli.

---

### Post by howefield on 2015-10-07
Thread moved to the "*MINT*" forum.

---

### Post by ogp on 2015-10-07
Howefield, 

Thanks for moving the thread, sorry for having put it in the wrong place!


Oli.

---

### Post by yancek on 2015-10-07
If the computer is ten years old, the hardware might not be capable of running Mint.  That depends to a certain extent on which Mint you are using as their are several options.  You can see the various versions at their site below.

[http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php)

Minimum hardware requirements are shown at the link below.  Compare that to your hardware.

[http://blog.linuxmint.com/?p=2656](http://blog.linuxmint.com/?p=2656)

The reason you can't boot the installed Mint is because you did not install the Grub bootloader which is stated at the very top of the boot repair output.  There is no /boot/grub/grub.cfg file which is also needed.  At the end of the boot repair, it gives the option to "reinstall the grub2 of sda1 into the MBR of sda".  You don't seem to have any Grub files at all which is definitely not the default.  Probably the simplest thing to try although I would suggest checking/comparing hardware if you computer is that old.

---

### Post by ogp on 2015-10-08
Yancek, 

Thanks for your reply - that's very helpful. The machine runs a live session well enough and the specs are better than the minimum listed on the requirements so I think it should run Mint OK. It'll never be super-quick, but should be usable. I'm on 32-bit Mint MATE as that is the one that I use on other machines. 

Thanks very much for identifying that I don't have any GRUB files. It seems that what I need to do is create a GRUB for the installed software. If, from the live session, I mount sda1 to /mnt using: 

# sudo mount /dev/sda1 /mnt

and then try to access it using: 

# sudo chroot /mnt

I get the message "bash: /usr/share/bash-completion/bash_completion: No such file or directory"

... and the command prompt (mint / #) won't recognise a number of commands, including grub-install or update-grub. 

Again, if you can help then I'd be grateful - thank you.  


Oli.

---

### Post by yancek on 2015-10-08
Check the Ubuntu site below and go to the section ov "via Chroot", Section 2.2.5.  After mounting it, make sure you run the command under number 10 in that section then run the sudo chroot and sudo grub-install and sudo update-grub and exit chroot and reboot and try it.

[https://help.ubuntu.com/community/Grub2/Installing#via_the_LiveCD_terminal](https://help.ubuntu.com/community/Grub2/Installing#via_the_LiveCD_terminal)

---

### Post by ogp on 2015-10-08
Yancek, 

Thanks again. I've tried that, taking particular care to type the string at point 10 correctly, and when I put in the command at point 12, namely: 

#grub-install /dev/sda 

... it gives the error "bash: grub-install: command not found". 

If I do it as superuser, i.e. use: 

#sudo grub-install /dev/sda 

It gives the message "bash: sudo: command not found". 

It gives the same error message for "update-grub" (i.e. "bash: update-grub: command not found"). 

What am I doing wrong? And thanks again for your help. 


Oli.

---

### Post by yancek on 2015-10-08
Are you using the Mint usb to boot, the one you used to install?  I don't know why you would be getting that error as Mint like pretty much all the Ubuntu derivatives I've used does use sudo.

---

### Post by ogp on 2015-10-08
Yes, the same USB. (It's started via Plop Boot Manager, but the installation was started in the same way). 

It's not just sudo - it doesn't seem to recognise any command once you have chroot-ed into the installation. 

Thanks for your help anyway. 


Oli.

---

### Post by Rob Sayer on 2015-10-09
This may seem OT but I use Mint on my netbook, which had some hardware support issues with the wifi pre ubuntu 14.04/Mint 17.  I switched from Mint 13 to ubuntu on that machine once because I just could not get the support on their sites.  They just do not have the user base and hence expertise on their forums.

So from my perspective I'm wondering why you wouldn't just install Ubuntu if you can't even get mint installed and their forum hasn't helped.

I'm actually an ex ubuntu user at this point ... 2 mint 17 installs, though that can change ... but I wouldn't recommend anything but ubuntu for inexperienced users.  The only other distros I've seen that have as good support as Ubuntu are just not suitable for novices.

---

### Post by yancek on 2015-10-09
If you have not got this working and want to try again, run all the commands and copy them to a text file and then either post the text file here or a link to it.  Not sure what could be happening because Mint definitely uses sudo.  Your original post doesn't show any /boot/grub directory on the partition which usually shows up so I think it may be that the install didn't finish and am not sure installing Grub will resolve the problem.

---

