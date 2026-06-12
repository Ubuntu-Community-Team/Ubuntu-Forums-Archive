---
title: "Boot from USB"
date: 2014-06-27
forum: Installation &amp; Upgrades
---

### Post by devc on 2014-06-27
I want to remove Ubuntu. How do i boot from USB so i can put another OS in its place?

edit: i've got a bootable usb. I'm guessing i need to access the grub menu. But what do i need to type in there?

---

### Post by LastDino on 2014-06-27
What partitions do you have currently? 

To remove Ubuntu, most straight forward way would be to simply format its installed drives after backing up whatever you need. This may get rid of the grub too but if new OS you're trying is LInux too, it will install its own bootmanager so it wont be a problem. If it doesn't, you can still install grub separately.

Or you can try tool called OS remover if you can get your hands on it,

---

### Post by devc on 2014-06-27
I've changed my boot order to boot from usb. But seems to be overriding .. like it attempts to but then continues with ubuntu. Its not the laptop because i installed ubuntu from usb and i've tried the usb in my windows pc and it attempts to install the OS. 

How would i go about formatting everything. I'm not sure how it to do it when i can't attatch another usb?

---

### Post by LastDino on 2014-06-27
Then that is probably not an issue with Ubuntu or Grub for that matter. If there is bootable device detected and is set as primary option, it will boot. 

Maybe try playing with the options in BIOS under USB booting , like changing ZIP drive to HD and set it to first boot. Or try different USB port or different USB key if it is available.

---

### Post by ajgreeny on 2014-06-27
How did you make your bootable USB device?  Are you certain you made it properly and did not just copy the image.iso to it as a single file?

---

### Post by grahammechanical on 2014-06-27
Depending upon the layout of the partitions you could simply install that new OS into the partitions that Ubuntu is in. If Ubuntu is the only OS on the disk and the new OS is going to be the only OS then simply tell the new OS to install and use the whole disk. We get his option when we install Ubuntu.

But as you do not tell us the layout of your partitions or what other operating systems are on the disk or even the OS that you want to install, then any advice can only be general and not specific.

But you may know how to do what you want to do.

---

### Post by devc on 2014-06-28
Sorry guys for the late reply. I'm not that technical minded, i haven't been ignoring you when asked about partitions, i just don't fully understand it. The Laptop was brand new with windows 8 ( hated this OS). So i overwrote it with Ubuntu. As for partitions, if i'm correct i think its split in two, the part with the OS and the part for storing files - no other OS installed. What i did do yesterday was go through the disk management. I found a button to format it. Since then its done nothing but display the background picture. and occassionally the background would flicker ( go up and down) but that seems to have stopped now. The mouse is still working, but nothing to click.

I'm not sure what is going on, its been over 24 hours now, 500gb hdd. Is this STILL formatting? i'm scared to turn it off as i recently destroyed an external HDD by accidently turning the system off during format so i don't want to do that again. 

The OS i'm trying to install is windows 7. I know this is working on the USB because when i plug it into the laptop i'm using now to boot the installation starts. 

Hope someone can help, i don't want to destroy this laptops internal hdd. Its less than 2 weeks old!

---

### Post by devc on 2014-06-29
Anyone?? its been 48 hours and its still stuck on the background screen

---

### Post by Vladlenin5000 on 2014-06-29
> **devc said:**
> The OS i'm trying to install is windows 7.

As explained before, you can just boot whatever installation media you have for that OS and absolutely everything that needs to be done will be done by its installer, including the replacement of GRUB by the Windows bootloader.
Whatever was there before _has no relevance_ for what you want to do. Your questions have _nothing_ to do with Ubuntu. If you need further help please ask in the proper forum: [http://www.sevenforums.com/](http://www.sevenforums.com/)

---

### Post by oldfred on 2014-06-29
If a new system with Windows 8 it also is a UEFI system. Default install of Windows 7 is BIOS based install and installing that will destroy your Windows 8. 
UEFI requires gpt partitioning.
BIOS required MBR(msdos) partitioning.

But you can convert a Windows 7 flash based installer to UEFI install. No idea how you dual boot with UEFI. Best to review on Windows forums.

---

