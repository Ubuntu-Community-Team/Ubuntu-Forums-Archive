---
title: "Re-Install"
date: 2017-03-27
forum: Installation &amp; Upgrades
---

### Post by windowsfree on 2017-03-27
Hello,

I currently have a dual boot setup with Xubuntu 14.04 and Windows 10.  I want to remove Xubuntu and reinstall Ubuntu Gnome 17.04.  This is on a non-uefi setup.
I am wondering if I can put the Ubuntu Gnome USB drive in and reinstall over the current Xubuntu 14.04 install and not have any issues with boot loader.

Thank you for taking the time to read this.

---

### Post by RobGoss on 2017-03-27
Hello and welcome, it would probably be a better choice to use Windows disk management tool to format that Xubuntu partition, then use that allocated space to install the new Ubuntu 17.04

This guide may be of help
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)

---

### Post by windowsfree on 2017-03-27
Thank you for the reply, will attempt to do that.  I will lose boot menu I assume after deleting that partition in windows so I will not be able to boot back to Windows until I install Ubuntu Gnome.

thank you for the quick reply.

---

### Post by RobGoss on 2017-03-27
After you used the **disk management **tool to format that unwanted partition run the live installer for **17.04, **you should see the option to run alongside Windows, if you don't you may need to chooses the **something else **option and choose the unallocated partition for your installation 

If you choose the something else option, you will need to install the boot loader on the **MBR** partition in order to successfully set your dual boot system

You stated your system was not **UEFI** correct?

Note: I would also make a complete backup of your Windows system just in case something goes wrong

Hope this helps

---

### Post by windowsfree on 2017-03-27
I have images of both partitions, thanks!

---

### Post by yancek on 2017-03-27
If you know which partition(s) you currently have Xubuntu on, it would be simpler to just boot Ubuntu to install it to that/those partitions and select the checkbox to format them before installing.  Simpler if you have only one partition, just make sure you have any data saved.  With an MBR install, leave the bootloader setting to the default and it will install to the MBR and create an entry for Ubuntu and windows.  There really isn't any need to use windows in this scenario but it should work that way also.

---

### Post by windowsfree on 2017-03-27
thank you,  I was wondering if your suggested method would work also.

---

### Post by RobGoss on 2017-03-27
There are a few ways to accomplish this it would depend on how comfortable you are using either method it's great to have more the one choice

---

### Post by windowsfree on 2017-03-27
I agree.  thank you to all who replied.  Will advise which method used when I have opportunity to do the install.
My thought process is right now that both OS's are working, but it is time to move to new software.

---

### Post by RobGoss on 2017-03-27
Good luck with your installation

---

