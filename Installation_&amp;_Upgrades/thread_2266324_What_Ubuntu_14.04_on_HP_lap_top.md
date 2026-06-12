---
title: "What Ubuntu 14.04 on HP lap top"
date: 2015-02-21
forum: Installation &amp; Upgrades
---

### Post by gordon33 on 2015-02-21
Hello All

I  have been having problems with Ubuntu 14:04  start up disk.  

I did a down load from the Ubuntu download web site to my HP laptop.  The Ubuntu 14:04 down load went to an F drive on the laptop.  I saved the down load to a DVD+R.  

When I look at the DVD+R disk their is a folder labeled "DVD Drive F Installed Ubuntu".  When you click on that folder the 10 to 14 Ubuntu 14:04 folders show up. 

I set the BIOS: Enabled Legacy , and moved both Legacy and UEFI Boot Order to INTERNAL CD/DVD ROM DRIVE

 **Is that F folder a show stopper?  Or, are the BIOS choices I have made poor,__**

This new (Dec. 1 2014) HP lap top came with Windows 8.1.  For the last 9 or 10 years I have used Ubuntu as operating systems on my other 3 computers.  I was able to do the install on the other 3 computers on my own.  Still....... a nube by most Linux operators standers.

Gordon33

---

### Post by Bucky Ball on 2015-02-21
You have downloaded the ISO. You need to burn the image to a disk to create a bootable install disk. Sounds like you might be trying to install by using the actual ISO folder files. 

You need to burn the disk image, restart the machine, go to the BIOS and set the machine to boot from the DVD (some machines allow you to hit F12 to choose a boot device).

Not aware of what software you are using to burn the disk image in Windows, but select to burn disk image, not to create a data disk. Dragging and dropping the ISO file to a disk won't work. You can also create a bootable USB by using [UniversalUSBinstaller]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") in Windows. This will install Ubuntu a little quicker. 

Apologies if you are burning the image correctly already. ;)

---

### Post by grahammechanical on 2015-02-21
> [COLOR=#000000]This new (Dec. 1 2014) HP lap top came with Windows 8.1. [/COLOR]

The machine came with Windows 8 pre-installed and that means that Windows 8 was installed in EFI mode. You need to install Ubuntu in Efi mode. You need to run the live/install session in EFI. Do not do this

> [COLOR=#000000]I set the BIOS: Enabled Legacy [/COLOR]

You will end up with a successful Ubuntu install that cannot boot Windows 8.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Oh, by the way, some manufacturers modify the UEFI boot system so that it only boots Windows. This is a failure to comply with the UEFI specifcation. But it is what some manufacturers are doing. 

[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

Regards

---

### Post by gordon33 on 2015-02-21
Hello  Bucky Ball, and grahammechanical


Bucky I clicked on burn CD,  I trust it was correct.  Is their a way to be sure the download is burned to the DVD?  The information "I set the BIOS: Enabled Legacy , and moved both Legacy and UEFI Boot Order to INTERNAL CD/DVD ROM DRIVE" was my attempt to get the computer to boot from the DVD,

grahammechanical I am okay  with wiping out windows 8.1.  I will check out the links you provided a quick look at them and it appears that information will be helpful.  I will post in a day or 2.

1gordon33

---

### Post by gordon33 on 2015-02-23
I made a new DVD and was sure to burn the DVD.  Then I went to bios and disabled the Secured boot and placed DVD in the first position.

During the install I chose to do the install along side the Windows OS.  I though all was well except when I restarted the computer the windows 8 booted up.  **If the duel boot was successful how would I get to the Ubuntu 14.04 OS?__**

---

### Post by gordon33 on 2015-02-23
Went to bios Devices and found I could make a selection Windows or Ubuntu.  So happy to have Ubuntu again.

---

### Post by Bucky Ball on 2015-02-23
They are both booting okay? Something odd is going on though as you should be getting a grub menu at boot. Could you open a terminal and:

sudo update-grub

See if it picks up Windows by rebooting. If no grub menu at boot (and it probably boots directly to one or the other OSs), try holding down the shift key at boot and see if that gives you the grub menu.

Glad you can get into Ubuntu again, though. ;)

---

### Post by gordon33 on 2015-02-24
Hello Bucky Ball

Thank you that gave me the Grub menu at boot up.

I was just starting to look for a way to select the operating system with out going to the bios.

Went to the terminal and  typed in "sudo update-grub".  Both Ubuntu and Windows were listed in the Terminal's response.  During the reboot the grub menu appeared with the widows and Ubuntu options.

Gordon33

---

### Post by Bucky Ball on 2015-02-24
Excellent news. ;)

---

