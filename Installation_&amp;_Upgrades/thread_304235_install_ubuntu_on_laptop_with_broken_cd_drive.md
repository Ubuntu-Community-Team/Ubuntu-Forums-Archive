---
title: "install ubuntu on laptop with broken cd drive"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by unfaigui on 2006-11-21
Hi everyone
I am a newbie. I tried to install ubuntu 6.06 lts on my laptop but the problem is the cd drive on it doesn't work.
I have seen this installation guide: [https://help.ubuntu.com/community/Installation/LocalNet](https://help.ubuntu.com/community/Installation/LocalNet)
However, it suggests to use it with another linux box to do it. I wonder if anyone knows how to use winxp box as the server instead.

thanks
unfaigui](*,)

---

### Post by kingcharles1666 on 2006-11-22
have you tried this?

[http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)

---

### Post by mikeapple on 2006-11-22
> **kingcharles1666 said:**
> have you tried this?

[http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)
Sorry to the post but this is very similar to what im trying to do.

I'm in the process of trying approach mentioned in that link. I've got grub to launch from boot.ini but I dont know exactly what to put in the menu.lst or the commands to use once grub is loaded to load the kernel and get it to boot.

This is what should be in my menu.lst

> 
title My Linux installer of choice
kernel   (hd0,0)/boot/your_linux_kernel_filename   distribution_specific_options
initrd   (hd0,0)/boot/your_ramdisk_filename

I have copied the contents of the xubuntu cd onto the hard drive so could anyone suggest what I need to enter for the location of the kernel and ramdisk?

Many thanks

---

### Post by unfaigui on 2006-11-22
thanks kingcharles1666
i will try it during the holiday.
and let you guys know how it goes.

unfaigui

---

