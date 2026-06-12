---
title: "Can't install Xubuntu. Getting error message. Help . . ."
date: 2011-09-05
forum: Installation &amp; Upgrades
---

### Post by Macfunky on 2011-09-05
I tried to install Xubuntu 11.04 on my acer aspire 1 today. I previously had Ubuntu Lucid on it but wanted to update it and try XFCE. I first tried installing it via a usb drive that i created with start up disk creator. During install i get this message -

"The attempt to mount a file system with type ext4 in SC212 (0,0,0), partition #1 (sda) at /failed. 

You may resume partitioning from the partitioning menu"

I have tried installing it to another usb drive with unetbootin and i am getting the same message. I'm not exactly sure what's going wrong. Any help would be appreciated. I had absolutely no problem with the netbook. It was working fine but now i can't get anything installed without that message and i'm unsure what to do.

---

### Post by 2F4U on 2011-09-05
Does that error happen while creating the usb stick or during installation on the netbook?

---

### Post by Macfunky on 2011-09-05
> **2F4U said:**
> Does that error happen while creating the usb stick or during installation on the netbook?

It happens during installation. I had no problems when creating an installable usb stick and i get the same error during installation from various usb sticks that have been created with both start up disk creator and unetbootin.

---

### Post by 2F4U on 2011-09-05
If you have a SSD in your Acer, this post may help

[http://gparted-forum.surf4.info/viewtopic.php?id=13825](http://gparted-forum.surf4.info/viewtopic.php?id=13825)

---

### Post by Stolgrove on 2011-09-05
I got a little out of that reading, but is there anything for a standard spin drive. have been trying to install from usb and have made little progress. 
I am installing on an Acer Aspire 1, I just threw in 1 GB ram and replaced my broken WD drive with one from an external. So I like to think its starting from scratch. Using the USB installer for Ubuntu (newest version). 
It runs the the install phase to the ubuntu loading window(similar to windows splashscreen), then goes through a stage where code is racing past on the screen. 
System pauses @ begin: preconfigure networking... .. /scripts/casper-bottom/23networking: line 31: can't create /root/etc/network/interfaces: nonexistant directory

After a minute, it jumps through more lines than I can stand to type on this phone

Mount: mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= bootarg.

BusyBoxv1.17.1 (ubuntu 1:1.17.1-10ubuntu1) built-in shell (ash)
Enter..help.....
(Initramfs) -

I have tried the switching usb ports, with small change and same end results, this will be the only OS running on the computer, and its a netbook, so usb is my only decent input.
Ran a memory test, 1 successful pass. 

* installing ubuntu 11.04 *

---

### Post by Stolgrove on 2011-09-19
> **Stolgrove said:**
> I got a little out of that reading, but is there anything for a standard spin drive. have been trying to install from usb and have made little progress. 
I am installing on an Acer Aspire 1, I just threw in 1 GB ram and replaced my broken WD drive with one from an external. So I like to think its starting from scratch. Using the USB installer for Ubuntu (newest version). 
It runs the the install phase to the ubuntu loading window(similar to windows splashscreen), then goes through a stage where code is racing past on the screen. 
System pauses @ begin: preconfigure networking... .. /scripts/casper-bottom/23networking: line 31: can't create /root/etc/network/interfaces: nonexistant directory

After a minute, it jumps through more lines than I can stand to type on this phone

Mount: mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= bootarg.

BusyBoxv1.17.1 (ubuntu 1:1.17.1-10ubuntu1) built-in shell (ash)
Enter..help.....
(Initramfs) -

I have tried the switching usb ports, with small change and same end results, this will be the only OS running on the computer, and its a netbook, so usb is my only decent input.
Ran a memory test, 1 successful pass. 

* installing ubuntu 11.04 *
 Solved this one easy... Just installed Lucid Netbook Remix, now learning how to install drivers for internet, then whatever else lays ahead

---

### Post by mörgæs on 2011-09-19
Good, please mark the thread 'solved'.

---

