---
title: "Ubuntu Server Installation."
date: 2018-05-26
forum: Installation &amp; Upgrades
---

### Post by turb03 on 2018-05-26
Hello everyone,

I got myself a small HP ProLiant MicroServer Gen8 that I can use to play around with and learn new stuff. I also got a Linux administration book, as I am pretty new to both servers and Linux. I tried with Fedora before it, but I didn't succeed so this time I tried with Ubuntu. I burned an Ubuntu 14.04 server image onto a USB, as that is the version they used in the book, and started installing it on the server. The installation finished successfully, I did everything and there were no error messages. After the installation completed though, I had to remove the USB and restart the system. I did that, but then the system couldn't boot Linux, it tried to boot from every source listed and then just froze on "Trying to boot from HardDisk C". I thought I may have done something wrong, but before putting Ubuntu on it I tried with Fedora and I ended up with the same thing. I read on some forums that this is an error with the server and some bios settings, but as I am pretty new to those kinds of things I'm not certain what exactly is wrong and how to fix it. If anyone has a solution or any suggestion, I would highly appreciate it! :D

Thank you very much;)

-turb0

---

### Post by yancek on 2018-05-26
> "Trying to boot from HardDisk C"

That's windows speak (C).  Which version of windows do you have?  Does it boot?  Did you shrink your windows partition before installing Ubuntu so that you had unallocated space on which to install?
If you used a usb to boot to install Ubuntu, did you change the boot priority back in the BIOS to the HDD?  Which option did you select to install the boot loader?  You should have used the default /dev/sda if you only have one drive.  Tht would have insalled the Ubuntu bootloader to the MBR (if you are using a Legacy system?) and created a boot entry for both Ubuntu and windows.

YOu can use the Ubuntu install usb to go to the site below and download and run the boot repair script per the instructions on the page.  Make sure you select the option to Create BootInfo Summary and post a link to the output here.  Do not try to make any repairs.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by turb03 on 2018-05-28
Hello yancek and thank you for the quick response! :smile:

The only OS the server has right now is Ubuntu, it doesn't have windows. I think it says C maybe because of the bios :/. When installing from the USB, I just choose boot from USB and then did a normal installation without modifying or changing anything. Everything was as recommended by the installation wizard. I also don't think it is a problem with the Linux installation but maybe something with the bios of the server, as the same thing happened when I tried to put Fedora. I can try to send you a screenshot or log of the system if you want, you just have to tell me how becauseI'm not completely sure how.

Thank you for the quick response and hope you can help me out again.:smile:
-turb0

---

### Post by yancek on 2018-05-28
Did the computer come with windows or another OS pre-installed?  If so, what was it?
Is this a new machine as in built within the last one to two yers?  Do you know if it is UEFI capable?
After you finished the install and removed the usb, did you reset the BIOS to boot from the HD?
If it is UEFI, you should have an option to boot from EFI file, that is if you installed EFI?

---

