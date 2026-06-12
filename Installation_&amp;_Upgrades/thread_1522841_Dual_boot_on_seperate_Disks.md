---
title: "Dual boot on seperate Disks"
date: 2010-07-02
forum: Installation &amp; Upgrades
---

### Post by drolfrawd on 2010-07-02
Greetings All.
I have a bit of a newbie problem. I have installed Windows 7 on a separate 160 gig drive.
I then unplugged it and Installed Ubuntu 10.04 x64 on 1 Tb drive.

Both work separately, But when I power on both drives Ubuntu boots straight up with no boot menu.

I did try several times with the normal dual boot, but the boot option for Ubuntu always failed.

I am desperate please help

Thanks

---

### Post by drolfrawd on 2010-07-02
Ok so i got it working, i read something similer on another post.
It's not pretty but it is working.

here is a paste of command and its outcome.

  	 	 	 	 	 	  lex@ubuntu-pc:~$  
 alex@ubuntu-pc:~$ sudo update-grub  
 [sudo] password for alex:  
 Generating grub.cfg ... 
 Found linux image: /boot/vmlinuz-2.6.32-21-generic  
 Found initrd image: /boot/initrd.img-2.6.32-21-generic  
 Found memtest86+ image: /boot/memtest86+.bin  
 Found Windows 7 (loader) on /dev/sda1  
 done  
 alex@ubuntu-pc:~$

---

### Post by darkod on 2010-07-02
What is not pretty about it? Because the windows disk was not connected during ubuntu install, it wasn't detected.
So after that you need to run update-grub with sudo permissions to re-scan for OSs.

---

### Post by ajgreeny on 2010-07-02
That is a standard command that you may use several times if you have grub2, particularly if you have a multiboot system with more than one linux distro and windows as well.  When you run that, any changes you have made to the other OSs will be sorted so that all should be bootable.

To my mind that is very elegant and a supremely simple way to update your bootloader without making a single manual edit to anything.

---

