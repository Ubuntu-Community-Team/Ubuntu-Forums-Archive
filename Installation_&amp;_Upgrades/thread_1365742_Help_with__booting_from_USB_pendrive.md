---
title: "Help with  booting from USB pendrive"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by 5socks5 on 2009-12-27
I am trying to install Ubuntu onto my 250 GB WD Passport hardrive so that I can boot Ubuntu on my Dell mini-laptop computer. The computer has only a 8GB internal hardrive and I want to keep the original Windows OS.

Here are the system specs:
OS: Windows XP Service Pack 3 Home Edition
Model: Dell Inspiron 910
CPU: Intel Atom CPU N270 @ 1.6GHz
RAM: 1GB
No CD or Optical Disk Drives

My problem comes from trying to install Ubuntu onto the 250 GB WD Passport. I cannot use a CD to boot the installation so I attempted to use unetbootin on a small USB pendrive so that I can boot the installation but my computer will not boot it.

I have tried changing the boot order to "USB Devices" first but all I get is an error message saying,
"Media test failed. Please check cable.
No Operating System found"

What can I do to solve this problem? Or better yet, what is an easier way to install Ubuntu onto my WD Passport.

---

### Post by earthpigg on 2009-12-27
> "Media test failed. Please check cable.
No Operating System found"

if you want to fix that, the first thing i would try is a different brand of thumb drive. some of them include 'features' for windows that also results in them not working as bootable thumb drives.

> Or better yet, what is an easier way to install Ubuntu onto my WD Passport.

you could use unetbootin on it :D make sure you select 'reserve extra space for personal stuff'.

the advantage of doing this is that you will be able to use the passport on any computer, as it won't configure itself specifically for that one single computer as it does when you click 'install' on the desktop.

---

### Post by 5socks5 on 2009-12-27
I don't see any option for reserve space for personal stuff. Do I not have the correct version of unetbootin?

I have windows version 377.

---

### Post by sgosnell on 2009-12-27
Easier than the WD is a good-sized SD card, maybe 16GB.  You don't have to plug it in and leave it every time you use the computer, and it's relatively fast.

What you need to do is make a bootable USB drive with unetbootin, 1GB is big enough.  Boot from that and then install Ubuntu to the drive you want.  There is no need to make the USB drive persistent, because you're only using it to install the OS.

---

### Post by 5socks5 on 2009-12-27
I cannot do that however because my computer is not booting from USB

---

### Post by sgosnell on 2009-12-27
So how do you propose to boot from the WD Passport?  It's a USB drive, isn't it?

---

### Post by 5socks5 on 2009-12-27
Yes that's my exact problem. I can't seem to figure how to make my computer boot off USB

---

### Post by sgosnell on 2009-12-27
It should be in the BIOS settings.  Enter setup at boot, however it's done on your machine, and there should be a Boot tab.  Go there, and see what the options are.  If the drive is connected, you should see it.  The Dell netbook will certainly boot from USB, but you need the USB drive connected at boot before it will see it.

---

### Post by 5socks5 on 2009-12-27
It is connected before boot and the bios settings are configured correctly however it keeps giving me that error message .

---

### Post by sgosnell on 2009-12-27
Well, naturally.  You have to put the operating system on the drive before you can boot from it.  The ideal way is to get a USB flash drive, 1GB or larger, and use unetbootin to put the LiveUSB/LiveCD image on it.  Connect it and the WD, boot from the flash drive, and install Ubuntu to the WD.  Again, an SD card is better, but if the WD HDD is all you have, and you want to use it, you can.

---

### Post by nerdtron on 2009-12-27
I installed my Karmic Koala using an 1GB MMC with a card reader (it is a bit slow but still did the job).
Within windows I downloaded the .iso of Ubuntu and then went to [www.pendrivelinux.com](www.pendrivelinux.com). I followed the instruction there to make a my removeable drive bootable.
Now for the BIOS part, I don't have any options to boot from usb but upon POST it said press F2 ( Im using an ASrock motherboard) to enter Setup and F11 for Boot Options. So i pressed F11 and it showed me the boot options: WD hard disk, Samsung hard disk, DVD Rom and finally USB Generic Card. I chose the usb drive and booted Karmic successfully. Then the installation to my hard drive followed. Thats it!

Just sharing...maybe it can help something :-D

---

### Post by dondano on 2010-01-08
Hello, I am having exactly the same problem trying to install ubuntu on a Packard Bell Easynote BV35.

I have tryed using two different pendrives (Sandisk and PNY attache) and I get the same error message you mentioned with both of them.

Could you sort the problem out?

Thank you

---

