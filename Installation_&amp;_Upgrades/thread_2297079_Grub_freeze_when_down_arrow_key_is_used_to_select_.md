---
title: "Grub freeze when down arrow key is used to select boot option"
date: 2015-10-01
forum: Installation &amp; Upgrades
---

### Post by seasoul2 on 2015-10-01
Hi, all talents,

I am helping one of my clients to install ubuntu alongside windows 7 on a server.

windows and ubuntu are installed on a SSD. Two other hdds are configured as raid for data storage.

After ubuntu installed, grub can recognise windows partition and include the boot options as Windows 7 (loader).

It is fine to boot into the default system ubuntu. 
But when I want to boot into windows, I use down arrow key to scroll down the list as usual, grub will freeze when it highlights the second option
(Advanced options for ubuntu), i.e., the menu item for submenu.

Reinstall ubuntu will not help.

I tried to figure out what happens by installing windows and ubuntu on my laptop. But everything went well  without any problem.

Anybody has an idea how to solve this grub problem?

BTW, using boot repair will not help, bringing the system to a command input grub.

---

### Post by VMC on 2015-10-01
Copy&Paste grub.cfg back here, so we can see whats up with the submenu.

---

### Post by yancek on 2015-10-01
You might need to post more detailed information and the easiest way to get that since you can boot Ubuntu, is to go to the link below and download and run the boot repair.  Make sure you select "Create BootInfo Summary" and not try any repairs.  A good idea to save the file as it is very informative with regard to your computer drives/partitions and boot files.  You can post it here and someone should be able to make a suggestion.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by seasoul2 on 2015-10-01
Yes, I will come back when my client is back from conference.


> **yancek said:**
> You might need to post more detailed information and the easiest way to get that since you can boot Ubuntu, is to go to the link below and download and run the boot repair.  Make sure you select "Create BootInfo Summary" and not try any repairs.  A good idea to save the file as it is very informative with regard to your computer drives/partitions and boot files.  You can post it here and someone should be able to make a suggestion.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by seasoul2 on 2015-10-10
Hi, yancek and all others,

I have got the bootinfo summary as this url

[http://paste.ubuntu.com/12737127/](http://paste.ubuntu.com/12737127/)

Any idea of what is going on?

Or the partition table has been messed up?

Thank you all.

> **yancek said:**
> You might need to post more detailed information and the easiest way to get that since you can boot Ubuntu, is to go to the link below and download and run the boot repair.  Make sure you select "Create BootInfo Summary" and not try any repairs.  A good idea to save the file as it is very informative with regard to your computer drives/partitions and boot files.  You can post it here and someone should be able to make a suggestion.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by yancek on 2015-10-10
Are you saying that you are not able to get past the "Advanced Options" line in the menu, that you cannot get to the windows 7 on sda1?  I notice that your image in the initial post shows only the entry for windows on sda1 but your grub.cfg file shows two windows entries?  The boot repair shows GPT on all the disks except sda where your Ubuntu and windows are installed.  Not sure if that is the problem or if it has something to do with RAID?

---

### Post by seasoul2 on 2015-10-11
Updated, 15.04 does not work either.

Hi,yancek

The image I attached is from my laptop installation but not this problematic server. I am using it just want to show the grub entries sequence. 
I am suspecting it is not because of RAID configuration or hybrid legacy and GPT disk because I have enabled CSM.

I found this post very similar to my problem.

[http://ubuntuforums.org/showthread.php?t=2226621](http://ubuntuforums.org/showthread.php?t=2226621)

When I add 'GRUB_PRELOAD_MODULES="usb usb_keyboard ehci ohci uhci"' to /etc/default/grub, ran 'grub-mkconfig -o /boot/grub/grub.cfg' and subsequently 'update-grub2'. My USB keyboard now worked fine in the Grub menu, the same error "grub error: disk (hd0,msdosx) not found" happens but the keyboard arrow can move up and down freely.

So I guess it is because of the external usb keyboard problem. I do not know if it is specific to Ubuntu 14.04. If so, maybe I will go to 15.

---

