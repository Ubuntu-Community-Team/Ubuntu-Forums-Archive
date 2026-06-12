---
title: "USB Boot Problems"
date: 2011-08-31
forum: Installation &amp; Upgrades
---

### Post by chome4 on 2011-08-31
Downloaded the latest iso file for version 11.04

Used a program called 'Yumi' that found the local version of this file which corresponded to the version I chose from the drop down list.

Go!.....

Made sure the computer was set to look for any USB device attached before the DVD drive and hard disk.

After the process had finished, I rebooted the pc and was presented, not with a menu, but the word 'boot' followed by a colon and flashing cursor.

Got the same when I followed the instruction on the official Ubuntu site which recommended another program similar to Yumi.

Any ideas?

Cheers.

---

### Post by Basher101 on 2011-08-31
wait wait wait...so you made a Live USB and wonder why you have no "bootloader" ? thats normal if thats what makes you worry. If you want to get a bootloader to the USB you must do a full install on it (With another Live USB or live CD). I will guide you on the installation onto a usb stick if ya want.

---

### Post by chome4 on 2011-08-31
> **Basher101 said:**
> wait wait wait...so you made a Live USB and wonder why you have no "bootloader" ? thats normal if thats what makes you worry. If you want to get a bootloader to the USB you must do a full install on it (With another Live USB or live CD). I will guide you on the installation onto a usb stick if ya want.

Hi.

The instructions made no mention of 'bootloader' and just guided me through a couple of clicks...

At what stage/how do I add this bootloader. Any guidance gratefully received!

Thanks in advance. I'm doing this on a Windows Vista machine, by the way but can try it on the actual Ubuntu pc, too.

---

### Post by Basher101 on 2011-08-31
First off sry cause i somehow lost your thread....second do you just want to "take a look" at ubuntu or actually make use of it? if just looking at it is what you want for now, your live USB is fine for that. Just keep pressing try ubuntu instead of installing.

---

### Post by chome4 on 2011-08-31
As I mentioned, my 'live usb' doesn't work. I don't get the option menu. All I see is the word 'boot' and a flashing cursor.

---

### Post by Hakunka-Matata on 2011-08-31
Hi, Welcome to the forum.
download and install unetbootin, (link in my signature) it is a reliable program for burning liveCD/USBs.
I suggest you download [ubuntu-11.04-desktop-i386.iso]("http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso") 

and try again, good luck

---

### Post by chome4 on 2011-08-31
> **Hakunka-Matata said:**
> Hi, Welcome to the forum.
download and install unetbootin, (link in my signature) it is a reliable program for burning liveCD/USBs.
I suggest you download [ubuntu-11.04-desktop-i386.iso]("http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso") 

and try again, good luck

Here's what happened:

Ran unebootin and pointed it to the downloaded iso file. Specified the e: drive on this particular pc, where the usb drive is connected. After the install took place, I rebooted and made sure the usb drive was first to be booted. I got:

Error: No configuration file found

No DEFAULT or UI configuration directive found

boot:_

This happens time and time again.

---

### Post by Hakunka-Matata on 2011-08-31
look at these two thumbnails - 
Does your usb drive directory and partition formatting look like these thumbnails?

---

### Post by chome4 on 2011-08-31
I've attached my equivalent images. Currently using a Windows Vista laptop....

---

### Post by Hakunka-Matata on 2011-08-31
Guess I'll have to do via Windows someday, I've installed many-many times but always on a Linux machine.  Is the usb marked bootable?  BootFlag?  could that be the problem?
maybe ubuntu's website will help:  [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by chome4 on 2011-08-31
I'll try on the Linux machine later on today.

---

### Post by aronin on 2011-08-31
Just type 'live' on that blank screen when you get on boot. You will have a live ubuntu and there is an option for installation.it worked for me

---

### Post by chome4 on 2011-09-02
Typing live just gives a 'cannot find kernel' error message.

---

### Post by Hakunka-Matata on 2011-09-02
tried hitting Shift Key successively once Bios finishes, continue hitting shift till you get to the boot menu, or where ever it is that it crashes?
That's instead of holding down shift key which can overflow the keyboard buffer.

---

### Post by chome4 on 2011-09-02
Nothing happens. There is no crash. Just the appearance of the word 'boot' and a flashing cursor.

Cannonical, who make these releases available, have a lot to answer for!

---

### Post by Hakunka-Matata on 2011-09-02
I don't know what to tell you, I always use Unetbootin, although I format the flash drive using gparted ahead of time.  I do everything on a linux machine too.  I download the .iso file and md5sum check against the hash, and it almost always works, sometimes I have to reload the usb, but it's certainly never a problem like you're having.  I read about yumi, that's a whole different idea, that's a os on a flash, not what you'd call a liveCD, blah, blah, blah.,
format to fat32, 1GB is sufficient, boot and lba flag on the partition.  I'd do it over, and check everything.

---

### Post by chome4 on 2011-09-03
'cannot find kernel image' is a very big problem, based on the google searched I've done.

[http://www.google.co.uk/search?q=cannot+find+kernel+image+linux&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.co.uk/search?q=cannot+find+kernel+image+linux&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by Hakunka-Matata on 2011-09-03
grub can't find the kernel image where it was told to look for it, maybe a simple reinstall of grub to the mbr of drive with ubuntu on it will fix everything.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

download, run, and post RESULTS.txt file from boot_info_script.
see signature

---

### Post by chome4 on 2011-09-08
I've just got a new pc and I'm using the DVD drive to install Ubuntu but I'll still need to attend to this issue in the near future as soon as I get this new pc up and running.

Thanks...

---

