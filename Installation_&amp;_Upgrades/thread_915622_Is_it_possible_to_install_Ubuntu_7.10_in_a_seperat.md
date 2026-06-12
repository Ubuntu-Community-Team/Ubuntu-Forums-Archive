---
title: "Is it possible to install Ubuntu 7.10 in a seperate hard drive ??"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by arunb on 2008-09-10
Hi,

I have a Windows Media Center installation on my computer, this has a single 160 GB SATA hard drive, with 3 partitions.

I have another spare 120 GB SATA hard drive, I would like to use this drive exclusively for installing Ubuntu, so that I do not have to take a risk by installing ubuntu and windows in the same drive.

Is this possible ??

thanks
arunb

---

### Post by iaculallad on 2008-09-10
It's perfectly possible. Once you're finished installing Ubuntu, you'll be using GRUB to load your windoze OS. (If you like you have the option of installing it on a free partition in your 160GB drive.)

---

### Post by arunb on 2008-09-10
Thanks your advice helped. Boy I am beginning to love Ubuntu.

I managed to install Ubuntu 7.10 onto a USB 4GB pendrive, this I did by making the drive bootable using syslinux, then ran the Ubuntu LiveCD from the CDROM of my computer. 

I selected the install program in the desktop, in the partiotion selection table I selected the USB pen drive, all this worked well and I was able to install and run Ubuntu from the pen drive successfully. (in fact every peripheral in the system worked like clockwork)

Now the problem is when I restart the computer without the pen drive inserted, the computer instead of booting from Windows Media Center kicks up an 'Error 21', with the message that GRUB was not found.

When I restarted the computer with the drive, I could get the Windows XP media Center option and was also able to run Windows successfully.

It seems I have to keep the USB stuck into the computer during booting.

Is there any way of shifting the GRUB files to C drive without upsetting Windows files, so that the computer shows the OS selection option even if the pen drive is not inserted.

My aim is to use Ubuntu and Windows, but since I have two computers I would like to make the installations portable, if everything works well I will finally use a 40 GB USB hard disk for Ubuntu...

Please help...

arunb

---

### Post by howefield on 2008-09-10
I have done something similar, only I disconnected the windows drive and installed Ubuntu onto the second drive, then reconnected the windows drive.This kept both operating systems completely seperate from each other. 

You shouldn't have to disconnect one drive, but no matter what I tried I couldn't get grub where I wanted it, so that was my workaround. The bios is set to boot from the Ubuntu disk and on the rare occasions I want Vista, I can use tell the bios to boot from the Vista disk.

---

### Post by arunb on 2008-09-10
The problem is the computer looks for GRUB in my USB pen drive and not in drive C:

So I have to keep the USB drive inserted for booting to work (even for Windows ). 

So how do I setup the computer so that it looks for GRUB in the C drive instead of the USB drive.

thanks
arunb

---

