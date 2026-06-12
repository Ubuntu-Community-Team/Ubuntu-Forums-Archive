---
title: "Using System Rescue CD"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by bothosnx on 2007-04-17
Hi all ...

I'm completely new on linux & still learning the basics. I've downloaded a **systemrescuecd-x86-0.3.4** because my ubuntu could not boot from my external USB. After booting with this ISO CD everything just ran by itself until i got into a root shell (complete startup i guess)... I'm not sure if this was completely running from the CD or it was running the installed Ubuntu from my USB HDD. Was not even sure if the shell is Ubuntu, how do i check this? Anyway, i rebooted (shutdown -r now) , removed the CD and restarted. Was back to the same problem, went straight to windows... 

Are there any step-by-step instruction on how to use this ISO rescue disc i've created?

---

### Post by rmemm on 2007-04-18
Check out all the linux doc at [www.tldp.org](www.tldp.org).  They probably have something.

I assume you ended up in the shell of the rescue CD.  Another good CD is Knoppix -- it's a full CD distribution so you can do your fixes in a GUI environment.  I also think the Ubuntu CD comes with a rescue mode which does basically what your rescue CD does -- can't really remember.  

Generally what I find is that if things are not to bad -- I personaly use Knoppix.  If my system is on the edge and Knoppix has problems -- or I know I have a serious problem like a failing hard drive or something, I use one of the command line CDs as they are easier on the system and may do less disk access for example.
 
The other thing -- use to be you could not boot linux from a USB drive -- I don't know if you can today -- have not heard much about it recently.  I'm sure it's possible to at least have most of your files on USB -- I just don't know if you can have them all there -- you may need the kernel and a few boot files on a small partician on your main drive.  Don't know for certain.

Also -- if you boot directly into windows when you startup normally -- sounds to me like you don't have a boot loader installed that supports a choice between linux and windows.  Normally you should get lilo or grub prompts -- then choose the system -- then boot into that system.

Rob

---

### Post by bothosnx on 2007-04-18
> **rmemm said:**
> Check out all the linux doc at [www.tldp.org](www.tldp.org).  They probably have something.

I assume you ended up in the shell of the rescue CD.  Another good CD is Knoppix -- it's a full CD distribution so you can do your fixes in a GUI environment.  I also think the Ubuntu CD comes with a rescue mode which does basically what your rescue CD does -- can't really remember.  

Generally what I find is that if things are not to bad -- I personaly use Knoppix.  If my system is on the edge and Knoppix has problems -- or I know I have a serious problem like a failing hard drive or something, I use one of the command line CDs as they are easier on the system and may do less disk access for example.
 
The other thing -- use to be you could not boot linux from a USB drive -- I don't know if you can today -- have not heard much about it recently.  I'm sure it's possible to at least have most of your files on USB -- I just don't know if you can have them all there -- you may need the kernel and a few boot files on a small partician on your main drive.  Don't know for certain.

Also -- if you boot directly into windows when you startup normally -- sounds to me like you don't have a boot loader installed that supports a choice between linux and windows.  Normally you should get lilo or grub prompts -- then choose the system -- then boot into that system.

Rob

Hi rmemm... I have went this rescuecd direction simply because my Ubuntu Linux CDs (ver 5.10)  would not give me these options (Rescue Mode)... Just doesn' t load anything close to this option. After loading the full linux OS using the rescue CD i've downloaded, can one mount the external USB or any drive from the root shell or should this be done right at boot (GRUB edit mode)? Thing is i've got the Linux installed on my USB external but won't boot. Used GRUB CD loader to force booting USB external but gives error saying 'unknown file system'. I think there may be steps in mounting or making file systems for this USB external if that's what is asking for... BTW, any steps requiring changes on conf/tab files won't work cause all the files are loaded/resides on CD disc hence this shell is running on CD.

---

### Post by rmemm on 2007-04-18
What your trying to do is complicated.  My advice -- read one of the how tos about this.  I found a whole bunch of them on google using the following search words:  "linux usb boot".  You can also get ubuntu specific how tos by just adding "ubuntu" to the previous 3 words.

After lookiing at these how-tos you'll have decide if you want to still do this -- I think it will be some work.

Regarding unknown file system -- I don't know -- could be the usb driver is not loaded or the driver for the file system your using is not loaded at boot time (which means it really needs to be either compiled into the kernel or part of an initrd image which is used at boot time).  Regarding boot loader -- my only point on this is that there must be a boot block on some device that loads linux.  It could be on your hard drive -- it could be on a cd rom or floppy used just to get things started -- and maybe it can just be on your usb key if your bios/firmware will boot usb devicies and you've place these before your hard drive in the boot search order (like your cdrom is).  

Rob

---

