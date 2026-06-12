---
title: "missing operating system after installation"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by faridym on 2010-12-31
Hi,

I'm new to Linux and wanted to get experience with Ubuntu Server for my new build NAS, because just a NAS OS wouldn't be enough for me. I wanted a server so I can also setup a PDC and webserver.

So currently I'm installing ubuntu server 10.04 onto my newly assembled server via usb stick(didn't build in dvd rom drive) I checked the BIOS before loading the OS onto  the computer and everything is detected. 


there's 1 thing that keeps bugging me. After installation i get a message that the install is complete and usb sticks and all devices should be removed to prevent it from booting the install again.

However when i remove the usb stick and I reboot the server I get the following message on the screen:

***missing operating system***

or

***can't find operating system***

When I do let the usb stick in, it boots into Ubuntu Server and i can see all my configurations that I made eventhough during install I chose to install it on the HD and paid attention to it I wouldn't touch the usb stick.

From here on i could configure the rest, like samba, and give my server an static ip address via the command line (this is so cool for me, to do from CLI, hahaha)


Back to my problem: what can i do to make my server boot from HD without that I have the usb stick in?

---

### Post by Sylchat on 2010-12-31
There are few possibilities about what happened: 
Perhaps you didn't install on a hard disk, but on the USB itself. When you boot up your Ubuntu, you can check which partitions you see and check if they're empty and containing system files.

I you find a partition that contains ubuntu (and which is not your USB key), you should check in your BIOS which device/hard disk is set for booting.

---

### Post by faridym on 2010-12-31
But is it normal, when I logon with the usb stick in it, and after logging in i take it out that I can still do configurations and installations? Because these won't get written to my stic

---

### Post by Quackers on 2010-12-31
It is possible that grub was installed to your falsh drive rather than your hard drive.
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by dino99 on 2010-12-31
> **faridym said:**
> But is it normal, when I logon with the usb stick in it, and after logging in i take it out that I can still do configurations and installations? Because these won't get written to my stic

suppose your /home is on hdd and the system on stick :(

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by faridym on 2011-01-02
Thanks guys, 

I think it had something to do with my flash drive.
Solved it already by using a temporary dvdrom drive. Now I also managed to install Server 10.10.
Thanks for all your comments and feedback. I appreciate it a lot as a newbie on Linux. If I knew the support and help would be this great, then I would have made the big step into Linux some years before. Well better late then never right.
Thanks again all of you

---

