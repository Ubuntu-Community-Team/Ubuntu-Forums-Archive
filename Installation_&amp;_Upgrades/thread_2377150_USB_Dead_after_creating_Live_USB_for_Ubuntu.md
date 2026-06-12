---
title: "USB Dead after creating Live USB for Ubuntu"
date: 2017-11-09
forum: Installation &amp; Upgrades
---

### Post by holahapi on 2017-11-09
My USB stick is showing no media, how can i Fix it?
I tried  CMD(Admin) Diskpart  clean command.
changing usb port
Window partition

Did not try "EaseUS Partition Master Free 12.5" yet, because I dont want to install extra program in my PC
 




This is how I get my frozen USB
--------------------------------------------------------------------------------
OS:Windows 10
Created Live USB  "ubuntu-16.04.3-desktop-amd64.iso" with UnetBootIn in my USB stick.
After the process, I tried to open the usb stick from "My Computer", then my PC when to blue screen.
After reboot, my usb not showing in boot menu.
After boot in window, the usb showing no media.(I can hear the insert system sound when I insert my USB)

---

### Post by RobGoss on 2017-11-10
Hello and welcome to the forums, Were did you download your Ubuntu ISO file from?

Try using **Pendrive** to create your bootable USB [https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) make sure your USB is in working order before you start your installation, sometimes were are not aware of defective USB's

---

### Post by holahapi on 2017-11-10
> **RobGoss said:**
> Hello and welcome to the forums, Were did you download your Ubuntu ISO file from?

Try using **Pendrive** to create your bootable USB [https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) make sure your USB is in working order before you start your installation, sometimes were are not aware of defective USB's



All of them download from their official websites.

The USB driver was working properly as Windows installation USB before.
Today, I tried Rufus to create the Ubuntu live CD, but not working,( but still able access to the USB driver)
Then I try Unetbootin without formating, and I get my frozen USB 

Thank you for the advice, I will try use **Pendrive** to create the Live CD in another USB drive.

---

### Post by sudodus on 2017-11-10
Check with md5sum, that the download was successful, that the iso file is good.

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Have you got any linux running or only Windows?

A very robust method to create a USB boot drive is **cloning**.

In linux you can use [mkusb](https://help.ubuntu.com/community/mkusb)

In Windows you can use [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

---

### Post by holahapi on 2017-11-10
My ISO's  md5sum is match.
I will try create it again tomorrow.

---

### Post by holahapi on 2017-11-11
Thank you for all the helps 
I finally sucess created with another USB drive by Rufus. (Use Diskpart to clean it before creation)

---

### Post by RobGoss on 2017-11-11
Were you able to get Ubuntu installed?

---

### Post by holahapi on 2017-11-18
> **RobGoss said:**
> Were you able to get Ubuntu installed?
I did not try to install Ubuntu.
Just want to use the Live CD to create Bitcoin Cold wallet.

---

