---
title: "Problem in Installing Softwares"
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by khichi on 2007-07-27
Hello Sir,

            I am trying to install software on Ubuntu 7.04 Alternate version, but every time i doble click to install i recieve message like this by the installer,

    "dependency problems prevent configuration"

or when i try to use command line instalation i recieve this message

"
khichi@ubuntu:~$ cd Desktop
khichi@ubuntu:~/Desktop$ sudo dpkg -i ballz.deb
Password:
Selecting previously deselected package ballz.
(Reading database ... 86971 files and directories currently installed.)
Unpacking ballz (from ballz.deb) ...
dpkg: dependency problems prevent configuration of ballz:
 ballz depends on liballegro4.2; however:
  Package liballegro4.2 is not installed.
dpkg: error processing ballz (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ballz

"

This message occures every time i try to install any package. Please sir help me to solve this problem. I have installed Ubuntu using WUBI installer.

Thanks in advance.

Bye

---

### Post by coffeecat on 2007-07-27
It sounds as though you are making the very common mistake of picking up packages to install from the internet rather than using the free repositories that are maintained by the distro - in this case Ubuntu. Don't worry - almost everyone new to Linux does the same. Conditioned by Windows use they don't realise that most software installation is much easier in Linux than in Windows. Most, but not all.

A dependency is a package needed by the package you are installing - usually a library file somewhat analogous to .dll files in Windows. What you need to do is go either to Applications > Add/Remove or System > Administration > Synaptic Package Manager and see if the software is available there (via the repositories). If it is the package manager will handle dependencies for you and download them before downloading the app you want. Easy if you know how.

I haven't heard of ballz, but I found a 'tecnoballz' in Synaptic. If this is what you want, use Synaptic to install.

On those rare occasions when the app you want is not in the repositories, the clue is in the error message. In your case it's asking for liballegro4.2 which is listed in  Synaptic. So what you do is install the needed dependencies with the package manager and then install the app you want. But in this case I should imagine 'tecnoballz' is what you want.

---

### Post by khichi on 2007-07-27
Thanks for your reply, it is true that i am new on Linux, 

 About the software name you said true its tecnoballz but i renamed the name for typing the name easier in terminal, and its just an example of error in this software i got these errors in all softwares i try to install. My major problem is that Ubuntu didn't installs driver for my modem and i have no internet connection on ubuntu. Is there any other way to download dependencies of the software.

Please help me, i want to migrate to Linux.

---

### Post by coffeecat on 2007-07-28
> **khichi said:**
> i have no internet connection on ubuntu. Is there any other way to download dependencies of the software.

Please help me, i want to migrate to Linux.

The only way to download dependencies or any other software is to have internet connectivity. I presume, since you are posting to this forum, that you have internet connectivity through a Windows or MacOS machine. I presume you must have donwloaded the tecnoballz.deb file using this. Without internet connectivity in your Ubuntu machine you would have to download the dependency with the Windows/Mac machine (in this case liballegro4.2), transfer that to Ubuntu, install it and then install tecnoballz.

Although possible, believe me, you don't want to go down that route. Sometimes you get multiple dependencies, or you get a whole chain of dependencies. You go to install package A and it wants package B. You get package B and try to install that and it wants package C... and so on. :( With a package manager you don't worry about that - it's all done for you.

I really think the best answer is to try to get your Ubuntu system connected to the internet. You haven't said what type of connection you have, only that Ubuntu didn't have drivers for your modem. A few brief points:

1 **Dial-up**. Almost all internal dial-up modems are Windows-only so-called winmodems. They are not proper modems at all. If you have a serial port on your machine most, if not all, external serial modems will work quite happily with Linux.

2 **ADSL**. Most, if not all, USB modems are also really only designed to be used with Windows. You can get them to work in Linux, but it's very fiddly. The best option is to use an adsl modem-router. These can be configured with a web-browser so it doesn't matter what OS you use. This is what I use.

3 **Wireless**. Depends on the chipset. Some work out of the box with no trouble. Some are very difficult to set up.

Why not post details of your internet connection and what that modem is and let's see if we can get Ubuntu connected for you.

---

