---
title: "Trying to install full Ubuntu on 64GB flash"
date: 2019-04-03
forum: Installation &amp; Upgrades
---

### Post by tjharring on 2019-04-03
I have had it with Windows 10. My laptop is 5 years old, and obviously not state of the art. Every 6 months when Microsoft rams their features update on mine and my wife's system I have to spend several hours fixing what it damaged. I have used Linux in VMs, but I would like to try with full system resources. I am looking at 3 Linux distros Ubuntu, Fedora, and Opensuse. My laptop has i5 processor, 8GB ram, and a 1 TB HDD. 

I would like to do a full install of each OS on a 64GB flash drive. I created a live USB of Ubuntu, and it runs great, but I would like to be able to configure my printers, install some programs, and try it out over a period of time. I would like to do the same thing with the other 2 distros. When I try to install Ubuntu 18.04 to USB it takes more than 6 hours, and the system will not boot from that USB.

First question, why does it take so long to install? When I create VMs it takes around 20 minutes.
I will leave the second question, because I did not write down what I saw on my screen when it would not boot.

---

### Post by huff2 on 2019-04-03
You said that you already created a live USB of Ubuntu 18.04 and now want to do a full install of Ubuntu 18.04 to your hard drive? Just making sure I understand the problem. If you want to simply test these different versions then make sure that your live USB has persistent storage or else everything done in that live session will be erased. 

To boot from your USB, make sure that the USB is bootable and not corrupted and make sure that your laptop is set to boot from USB, this can be achieved in the bios, which can be accessed during start up. 

When you say, it takes long to install Ubuntu but when you create a vm it only takes 20 min are you talking about the download time for the ISO file? ie, it downloads to a usb faster from inside a vm than outside?

---

### Post by yancek on 2019-04-03
A typical install of Ubuntu from a DVD/USB to another drive should take about 20 minutes so there is something major wrong here.  If you actually did install Ubuntu to your second usb, it should boot if you set that particular usb to first boot priority in the BIOS.  Do you still have windows 10 installed on an internal drive?  Do you know if it an EFI install?  If it an EFI install the boot process is different.

---

### Post by tjharring on 2019-04-03
I am trying to install the full Ubuntu OS on a 64GB flash drive. It takes between 5-6 hours to complete the install. Creating a live USB with persistent storage will not retain hardware drivers for printers and such.
My system can boot from USB, but will not boot when I am done installing the complete OS. I would like to install the 3 different distros so I can use them to figure out which one I like the best. Once I decide I will install it along side Windows.

---

### Post by huff2 on 2019-04-03
What is the error message that you receive when trying to boot? I'm assuming you are trying to run the full Ubuntu version from your USB, then, run Ubuntu from your hard drive, if you like it (same with the other 2). You are correct about not being able to retain hardware drivers in persistent storage. My apologies.

---

### Post by oldfred on 2019-04-03
UEFI or BIOS?

USB3 flash drive in USB3 port?

I did a full install to SSD in USB3 port in just over 10 minutes which surprised me. My install to internal SSD is just under 10 minutes, but install to USB3 flash drive is about 40 minutes.
Writes to USB flash drives are slow. You can improve performance with some settings once installed.
Life of flash drives is relatively short compared to either HDD or SSD drives. Or good backups required.
I primarily use mine for emergency boot and test installs.

---

### Post by jdeca57 on 2019-04-03
If the question is simply how do I compare systems like Fedora and OpenSUSE with Ubuntu then you might consider Virtualbox. with 8G memory and a TB HD that should be possible and it solves the problem of boot and installation time. Ultimately the idea shouldn't be to boot from usb so I guess the goal is to install on de HD.Of course, an installation on usb tests the hardware but that's something a live CD/DVD/USB also does.

---

### Post by C.S.Cameron on 2019-04-04
What works for me is to disable the internal drive, plug in the target drive, boot the installer drive and install to the target as you would to internal drive.

How old is your computer? 

Is it BIOS boot or UEFI boot?

Once the USB is working, plug in the internal drive, boot the USB and run ```
sudo update-grub
``` to add the internal drive to the USB's grub menu.

---

### Post by oldfred on 2019-04-04
Many new UEFI systems have settings in UEFI to turn off a drive. Then you do not have to physically disconnect a drive inside the case.

---

