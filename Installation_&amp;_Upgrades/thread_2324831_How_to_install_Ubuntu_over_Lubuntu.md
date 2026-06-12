---
title: "How to install Ubuntu over Lubuntu?"
date: 2016-05-16
forum: Installation &amp; Upgrades
---

### Post by jeduke02 on 2016-05-16
A couple of days ago, I installed Lubunto on my laptop.  It dual boots to windows 10.  Now, however, I want to replace Lubuntu with Ubuntu.

When I go to do the install, how do I make this work?  I simply want to replace the Lubuntu OS, thats it.

---

### Post by CantankRus on 2016-05-16
```
sudo apt-get install ubuntu-desktop
```
...and choose ubuntu at the greeter.

---

### Post by jeduke02 on 2016-05-16
I already have the disk.  I started the 'install Ubuntu" but I dont understand which option I need to select that will overwrite the current lubuntu and preserve win10.

---

### Post by CantankRus on 2016-05-16
Can you still login to Lubuntu?

---

### Post by jeduke02 on 2016-05-16
Yes.

---

### Post by CantankRus on 2016-05-16
If you login to Lubuntu and in a terminal run...
```
sudo apt-get install ubuntu-desktop
```
You will have an option to login to Ubuntu or Lubuntu at the greeter when you logout.
See attached video.

---

### Post by jeduke02 on 2016-05-16
I dont have much space.  Id rather just remove the Lubuntu installation.  I also dont have the ability to use a lot of internet to download anything, so i want to install over the lubuntu installation with my ubuntu cd that Ive already created.  Plus your command asks me about being root, and I have no idea who or what that is or what the password is (and I installed the system).

Got the command to run with sudo.  It asks for the cdrom for Lubuntu, which I give it, and it gives me an error.  It wants it at /media/cdrom .... that doesnt exist.

---

### Post by CantankRus on 2016-05-16
When running sudo you will be asked for your login password.
Lubuntu is based on ubuntu using its own set of default applications, window manager, panel etc.
I don't dual boot so I'll leave it up to someone else more familiar with windows10 and uefi.

---

### Post by jeduke02 on 2016-05-16
OK.  Well, the command I used got to the point where it wanted the cd for lubuntu, which I gave it, but it proceeded with a string of errors.

---

### Post by sudodus on 2016-05-17
CantankRus describes how to make a system with both Lubuntu and Ubuntu (both desktop environments in the system system). It is possble but there are also draw-backs, for example that there are two tools for the same task (one that comes with Lubuntu and one that comes with Ubuntu). There might also be some conflicts in configuration files.

I had such a system in the version 12.04 LTS, 'Precise', and it worked but was a bit cumbersome. I have not tried it in more recent versions. But I have a 16.04 LTS, 'Xenial', system with Lubuntu and Xubuntu. And I am happy with it.

-o-

It is necessary to have a working internet connection to install a program package. Is there no connection to the internet? Otherwise I don't understand why the system wants the CD for Lubuntu. Are you upgrading to a new version? Just installing a new program package (in this case the meta-package ubuntu-desktop) should not need the presence of any CD.

-o-

If you want a clean Ubuntu system, boot the computer from the Ubuntu install drive (DVD or USB) and start the installer.

To replace Lubuntu (or any other operating system) with Ubuntu you can simply re-use Lubuntu's root partition, which you can do if you select ***Something else*** at the partitioning window of the installer. Let the installer format the partition (to remove Lubuntu).

If you have a home partition, I suggest that you do the same (format and reuse it). It it possible to keep the home partition with the settings and tweaks, but it might cause problems, that take more time to fix (than to get a clean Ubuntu installation and do the tweaking from there).

---

