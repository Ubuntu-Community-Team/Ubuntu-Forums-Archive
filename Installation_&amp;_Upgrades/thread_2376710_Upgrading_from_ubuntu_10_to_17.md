---
title: "Upgrading from ubuntu 10 to 17"
date: 2017-11-05
forum: Installation &amp; Upgrades
---

### Post by mr-mister on 2017-11-05
Hi! i have a desktop computer with ubuntu 10 on it, but no wireless hardware. i boutght  a tp-link wn8200nd usb adapter but, there are no drivers for it in this computer. If i plug it with ethernet and upgrade to the last ubuntu (or just upgrade), will i have the driver? (I know it's anti-linux to attempt to install it myself) Would the procces erase my previous data?

---

### Post by RobGoss on 2017-11-05
I would recommend doing a clean installation of the **latest version** of Ubuntu seeing** Ubuntu 10** support ended a long time ago. Once installed you can then try getting your internet connecting up and running. Run the live installer and see if you're able to make a connection. Report back if you have any trouble

Ubuntu has proprietary drives you can install if needed

---

### Post by ajgreeny on 2017-11-05
Probably not a possible upgrade; Ubunt-10.## was 7 years ago and the hardware may not even be up to running the new Ubuntu version which demands far greater specification than that old version.

I highly recommend that you clean install, and would suggest that you try either Lubuntu or Xubuntu instead, though by all means see how Ubuntu 17.10 runs live from a USB flash drive; I suspect that it will be too much for whatever hardware you have, though tell us more about it and we can advise you better. 
The recommended hardware requirements for Ubuntu-17.10 are:-
> Recommended system requirements:
    2 GHz dual core processor or better
    2 GB system memory
    25 GB of free hard drive space
    Either a DVD drive or a USB port for the installer media
    Internet access is helpful

---

### Post by mr-mister on 2017-11-05
Thanks for the advice! the problem with clean installing would be that i'd loose my old files. If an upgrade from 10 to 17 where available (with a sudo apt-get upgrade or something like that), would it keep my files? Alternatively, if i install Lubuntu, or ubuntu 17 from a usb flash drive could i mount my previous partition of / instead making a new one? What do you think?

---

### Post by RobGoss on 2017-11-05
> **mr-mister said:**
> Thanks for the advice! the problem with clean installing would be that i'd loose my old files. If an upgrade from 10 to 17 where available (with a sudo apt-get upgrade or something like that), would it keep my files? Alternatively, if i install Lubuntu, or ubuntu 17 from a usb flash drive could i mount my previous partition of / instead making a new one? What do you think?

I'm almost certain if you try upgrading from **10 to 17.04** or other distributions from within the system you will run into problems. I would just backup any important file and after you do a clean installation just transfer those files over to the new system.  What are the specs for your system I know it was recommend to use a lighter version but were really don't know what your specs are

---

### Post by Topsiho on 2017-11-06
I agree with the advise given by the other posters, except for the advise to do a clean install to Ubuntu 17. **Ubuntu 17 has a very limited lifetime** (6 or 9 months, I'm not sure) after which it is not supported anymore, and you'll have to upgrade to an other Ubuntu again. Better is to do a clean install to Ubuntu 16.04.3 LTS, which is the latest LTS-version of Ubuntu. LTS versions are supported for 5 years.
If you wait a few months, a new LTS version is released, 18.04, in April 2018.
The only reason to try 17 is to see whether your wifi is supported in 17, if it is not in 16.04.3. But except when the adapter is very new, I think it will be supported in Ubuntu 16.04.3
Before installing, backup all the files and data you would hate to loose, first. I think your computer will still run perfectly on Ubuntu 10, only don't connect it to the internet for that would be perfectly unsafe.
As stated already, there are lighter versions of Ubuntu around, such as Lubuntu, Xubuntu, and others, which you could try. Just experiment, enjoy this, and keep the best!

Topsiho

---

### Post by Impavidus on 2017-11-06
If the plan is to upgrade to 18.04 as soon as it's available, it doesn't really matter whether you run 16.04 or 17.10 in the meantime. 16.04 is better polished, but I wouldn't be surprised if the upgrade from 17.10 to 18.04 were more reliable.

But don't try to upgrade from 10.x. Just do a clean install. You can install it into your current partition, so if you have a separate /home partition or keep your documents on some other partition other than were the operating system is installed, it's easy to keep the documents. But make sure you have backups anyway. If your documents are on the same partition as your OS it gets a bit harder.

---

### Post by mr-mister on 2017-11-06
I'm sorry, i think i misled posted an incorrect title for the thread. Actually my interest isn't for 17, the main purpose is to obtain the drivers for the tp-link wn8200nd usb wireless adapter (i have not found a "natural" way to install them myself). Would 16.04, Xubuntu or Lubuntu provide them? Why is upgrading not an option? I think it only has a / partition, could i create a new one for /home ? I understand that /boot is where OS is installed. Plesae correct me. Thank you for the patience!

---

### Post by Geoffrey_Arndt on 2017-11-07
TP Link wn8200nd - - it's kind of like trying to install fuel injection into a 1948 Studebaker (e.g., the OLD version of Ubuntu 10)

Save your data off to a usb thumb drive (or several drives), get the new Ubuntu-Budgie iso (for version 17.10 just released) and do a fresh install.    Have an ethernet connection at first.    Get a reliable proven wireless dongle from Panda [http://www.pandawireless.com/](http://www.pandawireless.com/)  (about $10 on Amazon for the nano sized Ultra 150 b/g/n - - no drivers to install, just plug it in and it works).   I find the "Budgie" desktop to be the easiest and most intuitive for many folks . . . very simple, like a ChromeOS version of Linux.

PS:   /boot is NOT where the OS is installed.    The OS is installed at the next higher level (think of a ladder) which is represented as just / . . . . (/ is the top of the directory tree, and about a dozen subdirectories including /boot are below it).

---

### Post by wildmanne39 on 2017-11-07
There is no way to get ubuntu to work by trying to upgrade from 10.04 to 17.10, there are just to many major changes. You also never upgrade using a wifi connection because during the process of updating you are almost a sured to get disconnected because of the upgrade especially a long upgrade process like this one would be. 

We can not help in getting 10.04 to connect to the internet in good conscience because it would be so vulnerable to hackers.  If you try to go that route we will close this thread for your own protection.

---

### Post by RobGoss on 2017-11-07
There is no way to bypass the upgrade you will most certainly have to start clean it's your best option.

---

### Post by mr-mister on 2017-11-07
Ok, clean install it is then. Thanks everyone!

---

### Post by RobGoss on 2017-11-07
If you have any problems feel free to come back for trouble shotting

---

