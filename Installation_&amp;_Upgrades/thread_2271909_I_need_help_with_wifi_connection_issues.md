---
title: "I need help with wifi connection issues"
date: 2015-04-02
forum: Installation &amp; Upgrades
---

### Post by chris367 on 2015-04-02
hi. I am a new ubuntu user (former windows user.)

I've recently installed ubuntu 14.04 lts on a dell inspiron 1440

it took forever to get the wifi to work, but I finally was able to do so by installing a driver package called "linux-firmware-nonfree_1.14ubuntu1_all.deb"

i can't remember the name of my wifi adapter, or it's chipset. but this is the only driver that my computer seems to like.

after installing the driver via usb, and connecting to wifi a software updater program appeared on the desktop asking if I wanted to update all of the software on the OS.

the first time I did this it updated all of the software including linux-firmware-nonfree_1.14ubuntu1_all.deb

well when the driver was updated the computer lost the internet connection once again, and no longer could see it's wifi adaptar. So I erased Ubuntu, and reinstalled it (with linux-firmware-nonfree_1.14ubuntu1_all.deb again) and so far this is my current state.

how can I update the software from the software updater without destroying the wifi connection?

thanks

---

### Post by Vladlenin5000 on 2015-04-02
Hello and welcome.

Perhaps you should install the OS first and then troubleshoot the WiFi properly instead of trowing in an old package.

---

### Post by Vladlenin5000 on 2015-04-02
Here's the guidelines: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by chris367 on 2015-04-02
Vladlenin5000 that isn't possible. also I tried the most updated version of the driver. infact I tried several drivers that were supposed to be compatible with my adapter. the package mentioned above is the only package that works,  and the computer has no Internet at all without the WiFi driver. also I'd rather not do another reinstall of the OS because I have stuff on the drive now. however have not preformed the update. it took 18 hours to get this thing to see the WiFi adapter.

---

### Post by chris367 on 2015-04-02
reinstalling the OS isn't an option nor could I connect to the Internet without installing the driver. I just want to perform the update without destroying the WiFi integrity.

---

### Post by westie457 on 2015-04-02
This post might help you. [http://ubuntuforums.org/showthread.php?t=2247762&p=13140076#post13140076](http://ubuntuforums.org/showthread.php?t=2247762&p=13140076#post13140076)

---

### Post by chris367 on 2015-04-02
westie457 how could I successfully perform that operation after the update though? doesn't the command sudo apt-get...  require connectivity?

---

### Post by chris367 on 2015-04-02
westie457 also my computer does not like the b43-fwcutter driver. actually it really doesn't like it. it only works with the linux-firmware-nonfree package.  the reason (I'm pretty sure)  is because the adapter is a low power consumption adapter,  and a variation on the regular part under the same model number.

---

### Post by westie457 on 2015-04-02
Oops my bad, forgot to mention the need for an ethernet cable.
This is possible without a cable but is much more involved and time-consuming.

**Edit **Instead of installing firmware-b43-installer use ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install firmware-b43-lpphy-installer
```[/FONT][/COLOR]

---

### Post by chris367 on 2015-04-02
I'm sure I could handle it. I just don't know where to find the proper instructions for my machine.

---

### Post by westie457 on 2015-04-02
Do you have access to another computer that is connected to the internet or Windows on your Dell computer? Also you will need [for preference] an USB stick.

Let us know which then we can begin.

---

### Post by chris367 on 2015-04-02
I do. I have both.

---

### Post by westie457 on 2015-04-02
Before we attempt this procedure do you have your installation media to hand?
Have been doing some research and the required driver should be in the /pool/restricted/b/bcmwl folder.
Copy the .deb file to your desktop and copy /pool/main/d/dkms to the desktop.

Open a terminal and (copy/paste these commands one at a time) pressing 'Enter. after each one ```
cd~/Desktop
sudo dpkg -i *.deb
sudo modprobe -rfv b43
sudo modprobe b43
```

Wireless should now be working.

---

### Post by chris367 on 2015-04-02
I swear I've preformed this procedure on a clean install. I will try exactly as you have suggested if it is reversible,  but will this operation be reversible if it doesn't work?

---

