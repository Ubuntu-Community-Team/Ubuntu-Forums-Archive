---
title: "Problem with ubuntu 10.10 not seeing hdd"
date: 2011-02-10
forum: Installation &amp; Upgrades
---

### Post by mosh511 on 2011-02-10
Hey guys,

I am completely new to Linux and I'm trying to do my very first install and I'm having a problem. 

I'm installing it dual boot style, with windows 7, ubuntu on a separate partition. I tried to install with a cd version but got this error after restart;

BusyBox v1.13.3 (Ubuntu 1:1.13.3-ubuntu11) built in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) Unable to find a medium containing a live file system 			 		

So then I used unetbootin to make a bootable usb, and I can run ubuntu fine, but it doesn't seem to recognize my Sata HDD when I go into gpart or when trying to install. I don't have any experience at all with ubuntu or linux in general so any help would be greatly appreciated, as I'm very keen to get started with Ubuntu and learning a new OS, especially one that is open source.

Thanks in advance,
Michael

---

### Post by Quackers on 2011-02-10
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

