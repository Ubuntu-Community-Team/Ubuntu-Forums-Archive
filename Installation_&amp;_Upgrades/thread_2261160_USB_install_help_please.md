---
title: "USB install help please"
date: 2015-01-16
forum: Installation &amp; Upgrades
---

### Post by matt18 on 2015-01-16
Ello all. I have a win 8.1 machine that i use for school and work. However, for graphic design and other things, i need to use ubuntu. So how do i install it onto a 16gb or higher thumb drive and be able to install programs, updates and save data to the drive as well? I will be doing this through my win 8 machine. I just want to be able to boot right into ubuntu(not live, an actual installed copy) from the usb drive, make something cool in gimp or whatever and be able to save right to the home folder of the OS. I want it to be simple and clean.

How slow is it going to be when running from a usb? Slower than a VM? I will be running gimp, inkscape and what not. DO i need to get a special type of thumb drive to make it be faster?

thanks

---

### Post by mikewhatever on 2015-01-16
Sure it's possible, and people have asked about it: [http://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator](http://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator).
Basically, you need an installation media - DVD/USB, a target media - the 16GB thumb drive in your case, and a computer to run it on. 
The process is about the same as installing to an internal HDD, that is, boot from the DVD, click the Install icon, select the target media when prompted, and so on.
You have to go with the manual partitioning (usually the last option, aka "something else"), and change the location of Grub to the target USB device. That is about the only challenge to deal with, unless there are other problems.

"How slow" is very relative. The I/O is going to be limited by the USB device read/write speed, so booting and launching programs will be noticeably slower, and a faster device will make it somewhat faster, but not more then the USB bus speed.

---

### Post by oldfred on 2015-01-16
You can install in UEFI mode also. But you have to use gpt partitioning on flash drive.
I have used gpt on both my BIOS & UEFI boot flash drives.

A USB3 flash drive in a USB3 port will be best, but some systems do not boot from USB3 or maybe users had not turned on the boot from USB device in UEFI.

 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/](http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/)
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi)

      UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

       Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

 Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

---

### Post by yancek on 2015-01-16
> DO i need to get a special type of thumb drive to make it be faster?

If your computer has USB 3 ports, get a USB 3 flash drive.  If the computer doesn't have USB 3, then a USB 3 flash drive won't matter.

---

### Post by matt18 on 2015-01-16
hmm. ok interesting. thanks for all the info. I am just making sure what the best option is for me. I do have it running in vmplayer but thought it would run faster on a usb drive. Thanks for all the guidance. Now i just need to make a decision haha

---

### Post by yancek on 2015-01-16
It would be a good idea to take a look  at some tutorials specifically on installing Ubuntu such as the very detailed one at the link below.  Read the first part of the page explaining how Linux drives/partitions are named so you understand how to select the correct drive, the flash drive.  It will also work better if you use the "Something Else" option to give you more control

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by sudodus on 2015-01-18
> **matt18 said:**
> hmm. ok interesting. thanks for all the info. I am just making sure what the best option is for me. I do have it running in vmplayer but thought it would run faster on a usb drive. Thanks for all the guidance. Now i just need to make a decision haha

Running in a virtual machine might be the best alternative, particularly if you have a powerful computer.

Otherwise there are good reasons to use a fast USB 3 pendrive, even if you boot from a USB 2 port. See [this link]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085").

See also the following links for more details.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by matt18 on 2015-01-18
> **sudodus said:**
> Running in a virtual machine might be the best alternative, particularly if you have a powerful computer.

Otherwise there are good reasons to use a fast USB 3 pendrive, even if you boot from a USB 2 port. See [this link]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085").

See also the following links for more details.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

I do have a new laptop. 12gb ram ddr3 or higher. haha. it should have usb 3.0. its only 8 months old. haha.

thanks

---

