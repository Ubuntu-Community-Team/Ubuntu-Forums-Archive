---
title: "Ubuntu with Windows Installation questions."
date: 2015-05-10
forum: Installation &amp; Upgrades
---

### Post by jminor2 on 2015-05-10
I am going to install Ubuntu and want to keep Windows 7 on the machine as well.  I understand I need to install from a usb stick and am unclear on the instructions.  
Do I download Rufus and the Ubuntu ISO image to the computer, then run Rufus to open Ubuntu onto the usb, then restart the laptop to get to the boot menu
(f12) to install from the usb?  As Ubuntu installs I assume I'm given the options to do the partition stuff to be able to run both Windows and Ubuntu.
Are there other steps I need to be aware of?
Thanks,
John

---

### Post by RobGoss on 2015-05-10
Hello John and welcome, you seem to have the right idea as mentioned in your post above.

When you have finished downloading your Ubuntu ISO file you will then begin to burn it to a DVD or load it on a USB stick using a USB installer. After this process is complete you will then place the USB in your computer and boot up your machine, depending on your machine most will use F12 to bring up your boot options. If you want the USB boot option just choose that one and your good to go.

When you've chosen the USB option you will them begin your installation, it will give you a few options one which will be to run Ubuntu along side of your Windows OS if this is what you want just choose that option and it will do it all for you.

Just follow the prompts and you should be ok and your Ubuntu ISO will be installed.

Good luck and we're here to help if needed.

---

### Post by grahammechanical on 2015-05-10
USB stick or DVD it does not matter which

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

You have to decide which version of Ubuntu to install. The latest version is Ubuntu 15.04 but that only has 9 months support for security fixes starting from April this year. It is better to install 14.04.2 LTS as that has support until April 2019.

This will give you some idea of what you will see during the installation process.

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

Run the live session to see if all the hardware is recognised. When you select Install Ubuntu you will get these options

Install Ubuntu Alongside them [that is other operating systems]
Erase Daisk and Install Ubuntu
Encrypt the new Ubuntu installation for security
Use LVM with the new Ubuntu installation
Something Else

It is the Something Else option where we get to ability to choose specific partitions to install Ubuntu to. It is a more complicated installation process. The INstall Alongside option is simpler. 

If you wish to create space for Ubuntu yourself it is best to use Windows utilities to defrag Windows more than once making sure that Windows loads each time. Then Use Windows utilities to create space by shrinking/moving the Windows partition to create unallocated space.

Then during the Ubuntu installation process choose the Something Else option and first use the Ubuntu utility (Gparted) to turn the unallocated space into 2 partitions. A large one form UBuntu with the Ext4 format and a smaller one for a swap partition. And then you can direct the installer to put Ubuntu into the partition you have created.

Regards.

---

### Post by jminor2 on 2015-05-10
Thanks for the replies, just wanted to make sure I wasn't going to mess up my machine......
Ubuntu here I come.....

---

### Post by sammiev on 2015-05-10
It's always a great idea to have a backup of your data before making changes.

---

