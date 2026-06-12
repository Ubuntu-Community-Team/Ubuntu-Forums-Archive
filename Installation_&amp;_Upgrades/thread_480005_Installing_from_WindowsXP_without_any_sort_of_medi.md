---
title: "Installing from WindowsXP without any sort of media."
date: 2007-06-20
forum: Installation &amp; Upgrades
---

### Post by eelozano on 2007-06-20
Is there a simple way to install Ubuntu on an external drive from within WindowsXP?  I would just install Ubuntu as the default OS, but I have run into issues in the past with this Dell D620 and would prefer to mess around on the external drive while still using XP to get online and troubleshoot (this used to be much easier before I sold my other computers :( ).

Anyway I am looking for a fairly simple way to install Ubuntu onto an external from within WindowsXP.

---

### Post by louieb on 2007-06-21
Haven't used it myself but take a look at [Wubi - The Easiest Way to Linux]("http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html")
Only way I know to install Linux besides using a virtual machine.

---

### Post by abn91c on 2007-06-21
get wubi from here [http://wubi-installer.org/](http://wubi-installer.org/)
it installs just like a windows program, main thing defrag first and dont do a hard boot reset when asked to reboot, let the pc do it by itself. By the way you need a broadband connection since wubi will download ubuntu and install from the internet and it may take a while depending on you connection speed.

---

### Post by logos34 on 2007-06-21
I have found this howto to work fine on an install from windows to external usb hard drive:

**[https://help.ubuntu.com/community/Installation/FromWindows?highlight=%28installation%29](https://help.ubuntu.com/community/Installation/FromWindows?highlight=%28installation%29)**

Works for netboot and CD approach.  Double check the directory paths if you use the latter.

---

### Post by bardgd on 2007-06-21
An easy way is to install VMWare Server and then within it you can install Ubuntu.  I have just the opposite.  I am Running Ubuntu Server with VMWare Server running in it and then I have XP as a guess.  VMWare Server is free for both Windows platforms and Linux Platforms.  If you want to save your XP machine, ghost it.  Then you can run an utility from VMWare called converter.  It is free also.  If will create a new image from the ghost image.  You will need to have Ghost version 10.   Or if you have another computer, which you said you sold, but if you have a laptop you can run converter on it and have it connect to the XP machine and create the guest image.  The only thing you will need to do is when you bring up the XP on VMware you will have to reenter you Microsoft License.  But once you have the XP Guest image, you can burn it to DVD Rom and have a fast recovery.  If you buy a new computer, you install VMWare Server on it and then load the XP Guest Image and you are back up and running.  This is also a great way to simplify the process of moving from one computer to another.

---

