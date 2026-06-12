---
title: "Installing UBUNTU help"
date: 2011-05-16
forum: Installation &amp; Upgrades
---

### Post by teenspirit7 on 2011-05-16
Ok, So I'm currently On Windows XP professional and want to dual-boot with Ubuntu....

Right, so I downloaded first the ISO for ubuntu here:
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

And then proceeded to downloading the windows installer here:
[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

However after "Successfully" Installing, I do not get a choice to boot from ubuntu on start-up...

I have tried several things;

Re-installing - To no effect
Downloading EasyBCD, which tells me that I have No BCD file, and when I opened my Boot.ini file, it was blank...
Also, there is no folder C:\Boot....


Now I don't know what to do and am scared to re-start just incase it doesn't  boot to anything...

Has anyone got any Ideas?

Thanks!

Finn

---

### Post by collisionystm on 2011-05-16
> **teenspirit7 said:**
> Ok, So I'm currently On Windows XP professional and want to dual-boot with Ubuntu....

Right, so I downloaded first the ISO for ubuntu here:
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

And then proceeded to downloading the windows installer here:
[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

However after "Successfully" Installing, I do not get a choice to boot from ubuntu on start-up...

I have tried several things;

Re-installing - To no effect
Downloading EasyBCD, which tells me that I have No BCD file, and when I opened my Boot.ini file, it was blank...
Also, there is no folder C:\Boot....


Now I don't know what to do and am scared to re-start just incase it doesn't  boot to anything...

Has anyone got any Ideas?

Thanks!

Finn


I have never used the Ubuntu install that you downloaded. I usually just mount the .iso in Windows and run the wubi.exe

[http://www.slysoft.com/en/virtual-clonedrive.html](http://www.slysoft.com/en/virtual-clonedrive.html)

---

### Post by teenspirit7 on 2011-05-16
> **collisionystm said:**
> I have never used the Ubuntu install that you downloaded. I usually just mount the .iso in Windows and run the wubi.exe

[http://www.slysoft.com/en/virtual-clonedrive.html](http://www.slysoft.com/en/virtual-clonedrive.html)
Just trying that one now,

But I think it is exactly the same....

---

### Post by Dreigo42 on 2011-05-16
Did you want it installed inside of windows like a program or did you want a true dual-boot with two OSes to choose from? 

Wubi installs Ubuntu like a program. If you wanted to boot Ubuntu by itself, you would boot from a USB Drive that you burned the .iso to. (Windows 7 can do this using the built in ISO burner)
After booting, select "Install Ubuntu" and choose "Install alongside other OS" (or something to that effect).
You will then get the options to adjust partition sizes and such and set it up.
NOTE: Installing this way will install the GRUB bootloader on top of the windows one and put the two in a list to allow you to pick which one you want to use at each start up. This is something to know if you ever want to remove Ubuntu from this as you will have to replace the then missing Windows loader.

I have never used EasyBSD but have never had any problems installing in this fashion.

---

### Post by bcbc on 2011-05-17
EasyBCD is just for Vista/7.

Right click on My Computer, Properties, Advanced, Startup & Recovery settings. This will show you the boot entries, and the timeout. If you click the drop down box there should be an entry for Ubuntu, and the Timeout should be set to 15 or 30. If you need to edit boot.ini do it from there as well (but back it up first).

In most cases, it's the Timeout that is set to zero, so bumping that up to 15 does the trick.

---

### Post by teenspirit7 on 2011-05-17
> **Dreigo42 said:**
> Did you want it installed inside of windows like a program or did you want a true dual-boot with two OSes to choose from? 

Wubi installs Ubuntu like a program. If you wanted to boot Ubuntu by itself, you would boot from a USB Drive that you burned the .iso to. 

I did what collisionystm said at it has now worked, But does that mean it's still just present like a program?

When I originally booted from the CD it did not give me the option to install alongside, only to remove windows completely?

Thanks

---

### Post by bcbc on 2011-05-17
Wubi is a dual boot that uses a virtualized disk (without having to partition). So you have to reboot to switch between Ubuntu and Windows. Ubuntu runs natively (separately from Windows).

See the [Wubi Guide]("https://wiki.ubuntu.com/WubiGuide") for more info.

---

### Post by teenspirit7 on 2011-05-17
Thanks for your help,

Just out of curiocity; is there a reason why it wouldn't let my install Ubuntu in tandem from the CD?

---

### Post by bcbc on 2011-05-17
> **teenspirit7 said:**
> Thanks for your help,

Just out of curiocity; is there a reason why it wouldn't let my install Ubuntu in tandem from the CD?

Perhaps you already have 4 primary partitions. Take a screenprint of the Windows Disk Manager or, from Ubuntu, the output of:
```
sudo fdisk -l
``` (lower case -L)

That might have the answer

---

