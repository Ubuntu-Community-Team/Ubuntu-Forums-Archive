---
title: "Installation Failure on Tosh M200"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by rgreen001 on 2008-11-24
Hello,
I have a Toshiba Portage M200 (Tablet PC) with a brand new hard drive formatted on a Windows PC with NTFS. I'm trying to install Ubuntu 8.10 on it via an external DVD drive on a PCMCIA card (no internal drive).
The disc boots up and starts the install but stops with a cursing flasher at...


Loading please wait...

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1 Ubuntu6) Built-in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs)_


any help please???
Thanks

Robbieg

---

### Post by lemming465 on 2008-11-25
Starting the boot means the BIOS can see the DVD drive; dying in BusyBox means the generic Linux kernel can't see it, probably because your PCMCIA card isn't supported yet.  Could you convert to [a USB install]("https://help.ubuntu.com/community/Installation/FromUSBStick") instead?

---

### Post by doemawa on 2008-12-01
Have the same machine (Toshiba M200) with exactly the same result. I noted that before the initramfs prompt shows on the screen the boot process is trying to access the disk drive at a rate of approx once per second for a while. It then stops and shows the prompt.

Will play with BIOS settings tonight...

---

### Post by lemming465 on 2008-12-01
There is [some advice about SD card -> USB booting for Debian]("http://www.adebenham.com/laptop/toshiba_m200.html"); does that help any?

---

### Post by doemawa on 2008-12-03
After playing around a while it appears to me that after the first code loads from the CardBus connected CD_ROM and control is transferred to this code, there is no support for the CardBus connected CD-ROM. casper.log says "Unable to find a medium containing a live file system".
I'm afraid the CardBus connected device is a dead end street...

My next project is to have a look at PXE...

---

### Post by doemawa on 2008-12-10
OK had a go at a PXE install... with success! This is my experience:

I used the instructions on the following page: [https://help.ubuntu.com/community/Installation/WindowsServerNetboot]("https://help.ubuntu.com/community/Installation/WindowsServerNetboot") 

Started with installing 7-Zip and Tftpd32 as instructed and downloaded Breezynetboot.7z then followed the "Breezy Style" installation instruction... Before moving immediatly to step 7 as instructed I extracted the Breezynetboot kit - makes sense...

At step 7 I discovered an error at the fifth bullet: The instruction tells you to enter the location of the pxelinux.0 file... but only the name of the file should be entered here - the location should be entered at step 9!

As said, step 9 should be extended and the location of the pxelinux.0 file should be entered in the "base directory" field.

During the boot/load process some of the necessary files are loaded from locations relative to the base directory location. So leaving this field open results in "file not found" errors.

The client machine now booted without any problems and the installation started...

Unfortunately, my next experience was that during the installation process it appeared that the version of Breezenetboot.7z is out of sync with the release info that is pulled from the archive servers during the process. This is clearly communicated so at least I did not have to spend too much time diagnosing

I then proceeded to the "Hoary Style" approach....
I pulled a fresh copy of netboot.tar.gz from the net and extracted the file. Step 7 and 9 as per the remarks above.

Then booted the target machine.. 1 hour later the installation was finished!

Note: The instructions instruct you to create and move a lot of directories. It did not quite make sense to me. All that matters is that you pick a directory, extract the compressed file (leaving the directory structure intact), tell Tftpd32 what the name of the boot file is and in which base directory this file resides.

Enjoy!

---

