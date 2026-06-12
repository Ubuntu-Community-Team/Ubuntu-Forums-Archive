---
title: "I need to create a empty directory as my computer has both SSD and HDD. How to do?"
date: 2021-01-16
forum: Installation &amp; Upgrades
---

### Post by EngineerStrange on 2021-01-16
I want to create a empty directory and then setup etc/fstab.
Do I have create the directory before installation or after installing. It will be more help for me if you mention the whole steps till setup.

---

### Post by ajgreeny on 2021-01-16
Your question does not make much sense so please give us a lot more information. 
What OS do you have on it at the moment?
What OS are you installing?
Show us the current fstab file if you're already running Ubuntu.
What is your current hardware? If you already run Ubuntu show us the output of command ***inxi -Fzx***

---

### Post by EngineerStrange on 2021-01-16
I don't have ubuntu installed right. I have windows 10. I want to install Ubuntu . Device is thinkpad.

---

### Post by The Cog on 2021-01-16
/etc/fstab is a configuration file that you will find on the Ubuntu system disk after you have installed it. The file is created by the installer and describes which disks/partitions the system should use.
If you google for "install ubuntu 20" you will find lots of install guides.
If you can explain why you are concerned about this file in particular then maybe we can explain more.

---

### Post by ajgreeny on 2021-01-16
We still need much more information.

What size are the disks?
Which disk or disks are already in use for Windows?
Tell us as much about hardware as you can.

---

### Post by Hagar Delest on 2021-01-16
I guess that you mean you want to create partitions(s) to install Ubuntu in parallel with Windows 10 to have a dual boot.
As said above, plenty of tutos for that. You can search for 'partition install ubuntu', you should get plenty of topics. You'll have to resize the Windows partition if you want to keep it.
I would recommend at least one partition for the system (/) and one for the users documents, either you put the /home in that partition or you mount the documents partition in the /home afterward.
30GiB should be OK for the system (/) if documents are stored on another.

I also have a SSD and a HD. I put the system on the SSD and the documents on the HD (/home remaining in the system on the SSD).

---

### Post by SeijiSensei on 2021-01-16
I suggest an entirely different approach.

Install [VirtualBox for Windows]("https://download.virtualbox.org/virtualbox/6.1.16/VirtualBox-6.1.16-140961-Win.exe") on your Win10 machine.  Download an installation disk image like [this one for regular Ubuntu]("http://cdimage.ubuntu.com/focal/daily-live/current/focal-desktop-amd64.iso"), or [this one for a popular variant, Kubuntu]("http://cdimage.ubuntu.com/kubuntu/focal/daily-live/current/focal-desktop-amd64.iso").  Run VirtualBox and create a New machine. Follow the steps to create the virtual machine and point to the disk image file you downloaded when it asks for installation media.  Soon you'll have an Ubuntu or Kubuntu virtual machine running on top of Windows. See if you like it. (Also, install the "[Extension Pack]("https://download.virtualbox.org/virtualbox/6.1.16/Oracle_VM_VirtualBox_Extension_Pack-6.1.16.vbox-extpack")" for VirtualBox to get better video and USB support.)

Even with the Extension Pack installed you won't get the same video performance you do from running on bare metal. And passing through some USB devices can be a pain. But in general you'll get a full-fledged Ubuntu or Kubuntu experience just as if you had gone through the hassle of a dual-boot installation.  Just limit any gaming to the Windows machine itself.

[Oracle's documentation for VirtualBox]("https://www.virtualbox.org/manual/UserManual.html") is pretty extensive, and you can get a lot of help through Google searches. It's not complicated to set up a virtual machine.

If you can see the HDD from Windows, and it has more free space than the SSD, put the VirtualBox images on the HDD.  It will take a bit longer to load the virtual machine, but once it's in memory it won't matter much which drive it was loaded from.

If you have enough disk space, you can install [multiple]("http://cdimage.ubuntu.com/xubuntu/focal/daily-live/current/focal-desktop-amd64.iso") [flavors]("http://cdimage.ubuntu.com/lubuntu/focal/daily-live/current/focal-desktop-amd64.iso") of Ubuntu in separate virtual machines alongside each other. Then you can shop among them for a desktop you like.

---

### Post by Impavidus on 2021-01-16
This is referring to the issue in this thread: [https://ubuntuforums.org/showthread.php?t=2456520](https://ubuntuforums.org/showthread.php?t=2456520)

It's easier if you keep your issue in a single thread.

---

### Post by yancek on 2021-01-17
If you want to dual boot windows 10 and Ubuntu, the best starting point is to read the information at the link below which is the official documentation on the subject.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

