---
title: "install lubuntu from usb-stick"
date: 2018-08-19
forum: Installation &amp; Upgrades
---

### Post by gbnmvfx on 2018-08-19
I am trying to install Lubuntu 18.04 on an Asus laptop. I am using an USB stick because it doesn't have a DVD-drive. I followed this article about [EFI USB-Sticks]("https://wiki.ubuntuusers.de/EFI_USB-Stick/"), but didn't change the grub file. I am able to boot from the stick and select "install", but after some time I get multiple error messages and don't know how to continue :(.
[IMG]http://i65.tinypic.com/260s6ew.jpg[/IMG]

---

### Post by TheFu on 2018-08-19
And what, exactly, 100% accurately, are the errors?

Can't begin to guess anything without that info.

If there are instructions and those aren't  followed, someone might be able to explain things clearer. IDK.

In the meantime, can you use the "Try Lubuntu" option?  How does that work?  Networking fine?  Sound?  Video?

---

### Post by ubfan1 on 2018-08-19
Did you hashcheck the downloaded ISO and run the media-check on the USB after it was created?  Does the USB work on other ports, on other computers?

---

### Post by gbnmvfx on 2018-08-20
The error messages are:

[0.046760] mce: [Hardware Error]: CPU 0: Machine Check: 0 Bank 4: a600000000020408
[0.036772] mce: [Hardware Error]: TSC 0 ADDR fef61f40
[0.046784] mce: [Hardware Error]: PROCESSOR 0:506c9 TIME 1534684429 SOCKET 0 APIC 0 microcode 2c

BusyBox v1.27.2 (Ubuntu 1:1.27.2-2ubuntu3) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) Unable to find a medium containing a live file system


I get the same message, if I select "Try Lubuntu". I didn't change the grub file because the steps are marked as optional.
I looked up an instruction that enables me to hashcheck the ISO-Image, but that was a bit long and complicated. I downloaded the ISO-Image a second time and created a new boot-USB instead. I am surprised by the fact that it is working without any problems. What did I do differently? I used another image and I mounted the ISO-Image to copy the files to the stick. I used the package-manager to extract the files last time. I think that the last was the mistake. It's not finished yet, but I don't see any reason for other bugs to appear. Thanks for the help.

---

### Post by yancek on 2018-08-20
The image you posted initially would seem to indicate either a bad download or a bad 'burn' to the usb.  You need to do a hash check of the iso after download to verify that it wasn't corrupted.  That happens sometimes.  Not much point in putting a corrupt iso on a DVD or usb so verify that first.  If you have only a windows system and not Linux to verify the download, do an online search for how to do it with windows.

[https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)

You said you didn't 'change the grub file', what grub file?  Do you have another instance of Linux installed using grub?

> I used another image and I mounted the ISO-Image to copy the files to the stick.

The general method to take a Linux iso file and put it on a usb to make it bootable is to use software specifically designed for that purpose.  If I am understanding your last post, you mounted the iso and then copied those files to the usb, is that correct?  That could work if you have Grub on the machine and put a proper entry in the grub.cfg file.  I'm not sure I'm reading your post correctly?

---

### Post by gbnmvfx on 2018-08-26
> **gbnmvfx said:**
> I am surprised by the fact that it is working without any problems. What did I do differently? I used another image and I mounted the ISO-Image to copy the files to the stick. I used the package-manager to extract the files last time. I think that the last was the mistake. It's not finished yet, but I don't see any reason for other bugs to appear. Thanks for the help.
Lubuntu is working fine now.

> **yancek said:**
> 
You said you didn't 'change the grub file', what grub file?

The file "/boot/grub/grub.cfg" on the iso-image

---

### Post by TheFu on 2018-08-26
If this is solved, please use the "thread tools" button and mark it to help out the community.
If it isn't, there are reputable instructions here: [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0)
and
[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows)
and
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
I used google with "ubuntu make usb installer" as the search term.

---

### Post by gbnmvfx on 2018-08-27
Ah, I didn't know that I can mark the thread as solved :)

---

