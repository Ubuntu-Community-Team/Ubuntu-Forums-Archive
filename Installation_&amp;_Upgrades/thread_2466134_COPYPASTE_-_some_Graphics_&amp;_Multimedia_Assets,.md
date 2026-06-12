---
title: "COPY/PASTE - some Graphics &amp; Multimedia Assets, so work with them from Ubuntu Studio"
date: 2021-08-20
forum: Installation &amp; Upgrades
---

### Post by lsepolis123 on 2021-08-20
Following here: 
[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview)

and created a bootable USB Stick Ubuntu or Ubuntu Studio 21.04 with Persistence 60GB

Well, if COPY to this USB Stick Ubuntu Studio - MANUALLY from Windows 10 Pro PC, - **COPY/PASTE - some Graphics & Multimedia Assets, so work with them from** Ubuntu Studio 21.04, **well where is best to save them**, in the root - create a folder eg /media - of USB Stick Ubuntu Studio, or where...?

---

### Post by tea for one on 2021-08-20
I hope that I have understood the question correctly:-

Boot into your USB Ubuntu Studio (with persistence)
Use the file manager to navigate to your Windows drive
Copy the files
Paste them, for example, into your Downloads folder

Alternatively create a folder with a special name - your choice.

When you close your live session, your [COLOR="#0000FF"]copied[/COLOR] files will be available next time you boot Ubuntu Studio

Test boot, copy, save and reboot with something simple to build confidence.

---

### Post by lsepolis123 on 2021-08-20
Is any wat COPY in Windows 10... and view/use in Ubuntu Studio...?

---

### Post by ajgreeny on 2021-08-20
> **lsepolis123 said:**
> Is any way to COPY in Windows 10... and paste/view/use in Ubuntu Studio...?
I have corrected, I hope, your question but please let me know if I got it wrong.
However, if my correction is correct, I do  not think there is any way to paste from Windows into a live Ubuntu system which can not, of course, be running if you are booted into Windows, and to the best of my knowledge there is no way to mount or view the contents of a live system with persistence from Windows.

I must admit, however, that I know so little about Windows these days that I may be completely wrong about this so wait for other answers.

However, there are other ways to deal with this, for example by disabling fast-start in Windows to stop the hibernation state when it shuts down which is the default. This will allow you to save files to another NTFS partition, preferably not the Windows OS partition, when using your Windows system.
You can then  mount that NTFS partition in the live Ubuntu system and work on the files as you want to, and then save them back to the same place.

---

### Post by tea for one on 2021-08-20
> **lsepolis123 said:**
> Is any way(t) COPY in Windows 10... and view/use in Ubuntu Studio...?

While in Windows 10, copy the files to another USB stick (format fat32 or ntfs)
Safely remove the drive
Close Windows 10
Boot your Ubuntu Studio live USB
Plug in your other USB (as detailed in line 1)
Copy the files to Downloads (or your preferred folder)

It is somewhat long-winded and unnecessary.

What is the difficulty with post 2?

---

### Post by MAFoElffen on 2021-08-21
Just a note... Windows 10 cannot read nor write to a Linux filesystem. But Linux (Ubuntu is Linux) is smart enough to read and write to both (and more). This is what people are trying to explain to you.

You are doing it backwards.. Boot up on the Ubuntu flavor... and copy what you want from your Windows NTFS drives...

---

### Post by lsepolis123 on 2021-08-21
I confused
Because, I have created this bootable USB Stick Ubuntu Studio OS 21.04, in Windows 10, is There problem COPY Media Assets to a folder in this bootable stick??? and find them(media assets) after boot up in Ubuntu Studio OS 21.04...?

[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview)

---

### Post by ajgreeny on 2021-08-21
There was a time, I believe, when Windows could see and create only a single partition on a USB flash drive; I have no idea if that is still the situation, but whether it is or not, there is no way that you can COPY Media Assets to a folder in this bootable live Ubuntu system unless it is actually running and also was created as a persistent live system.

You are, I think, complicating the whole process that you want to use more than necessary.

Create a live Ubuntu system with persistence on a USB flash drive, run that on a computer that has Windows (or any other Linux distro; not sure about Mac) installed, and you will then be able to mount the partitions of the installed OS in the live system and read/copy/paste any files on the Windows system into the live Ubuntu. With persistence those pasted files will be retained permanently in the live Ubuntu system but you will not be able to see them when booted to windows even if the USB is inserted.

---

### Post by lsepolis123 on 2021-08-22
If shrink space and after create a media partition, in windows 10, on the usb stick for this media, probably i will be able see that partition and media Assets content, if boot in usb stick Ubuntu Studio OS... from main partition in usb stick...?

---

