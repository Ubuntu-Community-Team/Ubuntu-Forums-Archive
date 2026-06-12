---
title: "installtion of ubuntu on a trojan horse infested hp laptop"
date: 2012-11-16
forum: Installation &amp; Upgrades
---

### Post by annette927 on 2012-11-16
Hi all, I just registered on this website because I have got a trojan horse & rootkit problem on my HP laptop which currently runs xp. I cannot get rid of that problem and a reinstallation of an OS is required.
As I always wanted to rather use Linux and had already checked out Ubuntu I thought I could just download Ubuntu on a usb stick, plug the usb stick in and it would install itself.
However, through trailing through a lot of installation guides I am very confused now. I do not know very much about computers and all that special lingo.
Is there an easy way to install Ubuntu from a usb that gets rid of everything which is on the laptop for absolute beginners?

Any help will greatly be appreciated.
Thanks! Annette

---

### Post by snowpine on 2012-11-16
Welcome to the forums!

Here is an easy 1-2-3-4 guide with pictures: [http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)

Before proceeding make sure that 1) you have backed up any documents on the Windows you want to keep (they will be overwritten when you install Ubuntu); 2) you have given Ubuntu a thorough "test drive" as a live CD/USB (without installing) to make sure it supports your hardware and meets your computing needs. (I recommend 1 week trial before committing to Ubuntu/Linux.)

---

### Post by dannyboy79 on 2012-11-16
depends on what computer you're using to create the USB Stick to install from but here's a great guide.
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

and yes, once you get the usb stick made, when you boot the computer up using the usb stick as the boot device, there's an option to install ubuntu and have it wipe out the hard drive and install ubuntu fresh.

---

### Post by sandyd on 2012-11-16
You probably want to get Ubuntu on a USB stick using a tool named [unetbootin]("http://unetbootin.sourceforge.net/")

Download the Ubuntu iso seperately, and when done, point Unetbootin towards the iso, and make sure the drive letter specified is your USB Drive's. The USB drive should be at least 1GB in size, and should be formatted.

After unetbootin prepares the USB drive, it will ask you to reboot. Your computer (should) have an option for choosing what device to boot from on your bios screen (its one of those F* keys, like F12, F8 or something), and make it boot from USB.

Once your done testing it out, you can just click the "install ubuntu" icon on the desktop.

You can just choose to replace everything on the drive during the partitioning stage of the installer

---

### Post by annette927 on 2012-11-16
Hi all, thank you so much for your support so far. I am trying to understand whatever is on those mentioned links. However, my IT knowledge is very limited. For example one page asked me to choose download for Windows , Linus or mac or so, I do not know if I am supposed to Choose Windows because the Laptop has xp on it? Neither do I know how to configure my laptop to start from the usb stick. My laptop hardly shows any programs anymore, hardly anything works, Taskmanager does not even work, no internet, nothing. I am sitting on a different laptop here. Any more advice out there in laymans language while I try and read a bit more? Thanks annette

---

### Post by snowpine on 2012-11-16
If the "different laptop" you are using to download Ubuntu and create the USB stick is running Windows, then follow the instructions for Windows computers. :)

[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

(Needless to say, if it's not your computer, then you should get permission from the owner before installing this software.)

If you're lost on how to create a Live USB or Live DVD then you can purchase one for about $5 from a third-party vendor or sometimes find one in a Linux magazine at your local news stand.

The problems you're having with Windows don't really matter since you will be erasing Windows (and **destroying** any data  you have not backed up to an external drive!) when you install Ubuntu.

And please do yourself a favor and **test drive before installing** as I suggested above! Linux is a completely new operating system with a steep learning curve. If you prefer Windows then my recommendation is to do a fresh reinstall of Windows to cure the virus/trojan problem.

---

### Post by coffeecat on 2012-11-16
> **annette927 said:**
> For example one page asked me to choose download for Windows , Linus or mac or so,

Ubuntu comes on a large file called an ISO file which you burn to DVD or to a USB stick and then boot from the DVD or USB stick. It doesn't matter what operating system you already have on your machine, so I don't understand what that page is trying to say. You can download the ISO file from here:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

The link that snowpine posted in post #2 gives you a number of links on the right for instructions as to how you write that ISO to either DVD or USB stick using various operating systems. There should be something suitable for the machine you are using.

> **annette927 said:**
> Neither do I know how to configure my laptop to start from the usb stick.

You need to configure the BIOS to boot from a USB stick (or from the optical drive if you want to install from DVD). To get into the BIOS, you press a certain key as soon as the machine starts up and before it tries to boot up. On my HP netbook, I have to press the ESC key as soon as the HP splash screen appears, after which I can choose F10 from the startup menu to get into the BIOS. Since your machine is an HP too, it may use the same keys. If not, you need to check in the documentation that (hopefully) came with the laptop.

---

### Post by gordintoronto on 2012-11-16
With a Windows computer as a starting point, I have had 100% success with Pendrivelinux.

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

