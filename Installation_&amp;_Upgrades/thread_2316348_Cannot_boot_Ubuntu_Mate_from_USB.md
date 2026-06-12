---
title: "Cannot boot Ubuntu Mate from USB"
date: 2016-03-07
forum: Installation &amp; Upgrades
---

### Post by aaron126 on 2016-03-07
Hi there.

Over the last year or so I've been getting to know Ubuntu better, happily fixing any issues I come across as I go, and usually finding the answers in these forums. Before I ask my question I'd just like to say thank you to all that have eased my path, and given me a flicker of understanding. Thanks.

I've recently got stuck, but for the first time I cannot seem to find a fix, or at least one that is definitive. The answer is almost certainly here somewhere, but I can't find it ... I've become very confused as to how to  proceed. Help would be greatly appreciated. I am no expert, but am willing to get stuck at the command line ...




**Problem - cannot boot from USB**

I have a laptop (ASUS UL30A) with a working Dual Boot of Windows7 & Ubuntu14.04 (both 64 bit) - this is all good. I would like to test Ubuntu Mate 15.10 from a USB drive. I have downloaded the ISO, and used Tuxboot to write it to USB. This seems to have been done successfully. The USB in question is a brand new Sandisk Extreme USB 3.0 32GB. The laptop has a functioning USB2 port. When I start up the laptop, with the USB plugged in, the laptop just boots up from the HDD, ignoring the USB. When I go in to BIOS to investigate I see that the USB drive is there, but is recognised as a local disk, rather than a removable USB.



I have tried reformatting the USB (FAT32), but this makes no difference.

I have used other USB drives to do this kind of thing in the past without any problems. Am I being stupid?

 
After searching around, there seems to be talk of flipping removable bits, using 3rd party software to properly clean the USB, or simply just tellng me that the Sandisk drive is no good, and I should just get another USB.

What's my best way forward?

Thanks in advance,
Aaron

---

### Post by pfeiffep on 2016-03-07
My first attempt with Mate & USB resulted in failure to boot also. I can't remember exactly what I did to remedy, but I think I launched gparted and removed all partitions from the USB and then re-created the bootable Mate 16  with success.

---

### Post by QDR06VV9 on 2016-03-07
I have seen this before and I just used another application to burn the iso on the USB
Here are 2 I really like and use exculively

mkusb Howto make USB boot drives
[http://ubuntuforums.org/showthread.php?t=1958073](http://ubuntuforums.org/showthread.php?t=1958073)

And another one that has tools to pack with me
MultiSystem &#8211; Create a MultiBoot USB from Linux
[http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)
Now mltisystem will need xterm installed..Just a heads up.
And by the way i have 2 of the Sandisk Extreme USB 3.0 32GB
I think you have to format over their U3 tools they have pre-installed 
More here [http://forums.sandisk.com/t5/All-SanDisk-USB-Flash-Drives/bd-p/all-usb-ssd](http://forums.sandisk.com/t5/All-SanDisk-USB-Flash-Drives/bd-p/all-usb-ssd)

Regards

---

### Post by aaron126 on 2016-03-07
Thanks for the help. Very much appreciated.

I have just done 2 things.

1)   I used Gparted to delete the existing partition, and then created a new partition (FAT32). The drive looked clean afterwards.

2)   I added the mkusb ppa repository, installed it, and then used the GUI to burn the Ubunutu Mate ISO to USB. This seemed to succeed.

I've now restarted with the USB plugged in, and it is the same situation: the USB is ignored, and the system starts as usual. Inside BIOS, the USB can be seen listed as an HDD. On inspection the USB seems to contain the right files.

Next I will investigate the Multiboot USB & I will see if I can find a Sandisk U3 removal tool.

Thanks again for your help guys,
Aaron

---

### Post by sudodus on 2016-03-07
If the computer is ignoring the USB pendrive, I think there is another problem. You need to make the computer boot from it.

Is the computer booting in UEFI mode or BIOS mode? [Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

Maybe you can try according to the tips in this link: [Booting the Computer from USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

---

### Post by aaron126 on 2016-03-07
I have just entered the following in a terminal

test -d /sys/firmware/efi && echo efi || echo bios

result:   bios

---

### Post by sudodus on 2016-03-07
Good, it is usually easier to boot in BIOS mode.

Have you found a place in the BIOS menus, where you can select the boot order?

With the USB boot drive connected, boot, enter the BIOS menu, and try to put the USB drive at the top of the boot list. There might be one list for DVD, USB, HDD, netboot, and/or one list for the HDDs (where the USB boot drive might be recognized, and should be at the top) according to the last link in post #5.

---

### Post by aaron126 on 2016-03-07
Okay, first off, thanks very much for all the help guys. I've got things working ... ish.

I've gone in to BIOS again at start up, and reordered the HDD drives (not removable USB) so that the *HDD: Sandisk* is at the top. I tried this before and it didn't work. Now it does. I can boot up Ubuntu Mate, and am currently installing it somewhat recklessly over the top of my current Ubuntu install.

I'm still mystified as to why the drive is considered an HDD as opposed to a USB ...

---

### Post by QDR06VV9 on 2016-03-07
Hey Good Job aaron126..
Bios can be very perplexing as of late.
Enjoy your new system.
@sudodus Thanks for hand while I was away:D Cheers

---

### Post by aaron126 on 2016-03-07
You gotta love it when a plan comes together.

Thanks once again for everyone's help. I've marked the thread as *solved*, even though the USB-as-HDD thing is doing my head in.

Not sure if I should have gone for the install ... I think I got a little excited about getting the usb to work ... hmmm.

Nothing ventured, and all that!

Cheers guys,
Aaron

---

### Post by sudodus on 2016-03-07
Congratulations and thanks for sharing your solution, *aaron126* :KS

> ... why the drive is considered an HDD 

Both are mass storage devices, and look the same to some BIOS systems.

@*runrickus*, Thanks for the greeting, it is always nice to 'see' you at our Ubuntu Forums :-)

---

### Post by aaron126 on 2016-03-08
I've now completed the installation, and everything is working fine.

Thanks again,
Aaron

---

