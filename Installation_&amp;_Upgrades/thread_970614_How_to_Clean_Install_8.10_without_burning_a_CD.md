---
title: "How to Clean Install 8.10 without burning a CD"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by Settler on 2008-11-04
As the title says I want to clean Install 8.10 and format root directory and keep /home directory as it is. But I don't have any blank CD so what should I do?

Thanks

I have the alternate.amd64.iso will the live cd be needed?..

thanks again

---

### Post by ghjf345 on 2008-11-05
As far as I know, you *have to* burn a cd/dvd in order to install it.

You could order one of those free cds offered by Canonical through their ShipIt service ( [https://shipit.ubuntu.com](https://shipit.ubuntu.com) ), but I understand a delivery may take up to several weeks.

You can also consider upgrading your current version of Ubuntu to 8.10 ( [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) ), which doesn't need you to burn any cds. But I would first backup my data before I did that, just to be sure.

---

### Post by status001 on 2008-11-05
[SIZE="3"][FONT="Century Gothic"]I've not finished yet downloading Intrepid, but I installed Hardy without CD. I installed it using Wubi. Just have the iso file and a CD/DVD image mounting software like Daemon tools lite, poweriso etc. Mount the iso image with this kind of software, and then you will have Ubuntu CD on your computer. After completing the installation process in Windows environment it require a reboot as well and then finish the job inside the Ubuntu environment. In Ubuntu environment you don't need to mount the iso in order to finish the installation. But for certain software installation with synaptic, you will need to mount it. I use Kiso to mount the image in Ubuntu, but the problem is every time I mount it the name of the Virtual CD got changed. As a result synaptic doesn't recognise the CD and cannot install any program with Kiso. Though, I've found out a solution my self. Just search for a program into the Mounted CD and try to install it manually. Obviously you have to install the dependencies first. Find out the dependencies into the CD as well. Thanks.[/FONT][/SIZE]

---

### Post by null_pointer_us on 2008-11-05
> **Settler said:**
> As the title says I want to clean Install 8.10 and format root directory and keep /home directory as it is. But I don't have any blank CD so what should I do?

Thanks

I have the alternate.amd64.iso will the live cd be needed?..

thanks again

This worked well for me:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I used UNetbootin as recommended, and gave it the .iso file from the live CD. The program extracted the setup files from the .iso and copied them to a blank USB flash drive I had lying around. Then I just had to follow the three steps (in the guide) to activate the Ubuntu boot menu.

Note that you may need to change a BIOS option to make your PC try to boot from the USB stick before it tries to boot from the hard drive.

I'm not sure if the alternate CD will work, but I don't see why not. :)

---

### Post by saidinesh5 on 2008-11-05
i once found this very useful method cuz my old pc didnt support usb boot and i didnt have a dvd drive, so there was this application called grub for dos...using that i mounted the ubuntu iso file during boot time and hence done!!

here
[http://www.quicktweaks.com/2008/04/07/install-bulky-linux-distribution-without-burning-a-cd/](http://www.quicktweaks.com/2008/04/07/install-bulky-linux-distribution-without-burning-a-cd/)

---

### Post by richsheil32 on 2008-11-05
How do you mount an iso file

---

### Post by Settler on 2008-11-05
problem is solved.

---

