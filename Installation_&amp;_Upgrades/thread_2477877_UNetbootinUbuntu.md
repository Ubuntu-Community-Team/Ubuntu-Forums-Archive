---
title: "UNetbootin/Ubuntu"
date: 2022-08-09
forum: Installation &amp; Upgrades
---

### Post by 63245aa on 2022-08-09
Have a computer with Win XP installed that doesn't boot from USB. 
Used UNetbootin to install Ubuntu 22 directly to hard drive without a problem.
Now want to install Win 10 using UNetbootin again (have another  partition ready) and get message "Do you want to uninstall UNetbootin"
I assume this will remove Ubuntu.
Do I have to use a different program to install Win 10?
Thanks.

---

### Post by TheFu on 2022-08-09
You need to install Windows to the storage BEFORE installing Ubuntu, if you are trying to setup a dual boot.  Windows will wipe non-Windows OSes and it will setup file systems that don't get closed properly, which messes with Linux's ability to access those partitions.


Or .... 


you can skip all of this and start using virtual machines.  Windows runs well inside a Linux-based hypervisor, sometimes even faster than on hardware. Also, about once a year, a MSFT patch will break booting in a dual-boot setup, which running Windows inside a virtual machine won't have as an issue.

BTW, unetbootin is a little old school. There have been a number of other tools for the same purpose available the last 4 yrs with more features and support that unetbootin didn't have last time I looked at it.  Rufus, Etcher, mkusb, Ventoy, are the typical competitors these days. Which is "best" depends on your need. I don't use any. I prefer the simplicity of placing the ISO file directly on a flash drive unmolested by other tools.  This requires some knowledge of how storage devices are named, so probably not a good idea for someone really new to Linux.

---

### Post by ActionParsnip on 2022-08-09
Does the system have a floppy drive or optical drive? If so, there is a boot disk which can then boot usb
[https://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/](https://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/)

---

### Post by sudodus on 2022-08-10
> **ActionParsnip said:**
> Does the system have a floppy drive or optical drive? If so, there is a boot disk which can then boot usb
[https://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/](https://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/)

+1

Plop is still alive :-P

[hr][/hr]
Edit: By the way, please tell us some details about your computer, at least brand name and model.

It can help us help you. Otherwise we can only guess what will work well in your computer.

---

### Post by yancek on 2022-08-10
>  I assume this will remove Ubuntu. 

Yes it will and it is explained at the bottom of the Unetbootin home page.  Also on their home page, it is explained that Unetbootin is used to create bootable "Linux" usb drives and is not expected to work with windows.  You can do this manually or do an online search to create bootable windows 10 installer. 

[https://unetbootin.github.io/](https://unetbootin.github.io/)

---

