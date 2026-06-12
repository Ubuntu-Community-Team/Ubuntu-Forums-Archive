---
title: "Ubuntu minimal: no internet connection"
date: 2015-10-02
forum: Installation &amp; Upgrades
---

### Post by ric_Poirier on 2015-10-02
Hi everyone,

I installed ubuntu 14.04 32-bit using a minimal iso, in cli mode. During the installation, I was able to successfully connect to my Wifi and download the necessary packages. After the installation, I plugged my computer with an tested Ethernet cable but was not able to connect to the Internet (a ping at [www.google.com](www.google.com) was not recognized). So right now, I am unable to install anything or update/upgrade anything.

I ran ifconfig, and wlan0 and eth0 showed up, but there was no activity.

Is this normal behaviour? How could I connect?

Thanks,

Éric

---

### Post by sudodus on 2015-10-02
I have installed Lubuntu and Xubuntu Core using the Ubuntu mini.iso. I had a wired connection (ethernet) during the installation, and it worked without problems also after rebooting. There are instructions about the network at this link

[MinimalInstall#Unmanaged_Wired_Network](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Unmanaged_Wired_Network)

Did you install a custom set of packages, different from what is available via the desktop iso files? Are you running a graphical desktop in the final installed system, or is it running in text mode?

---

### Post by ric_Poirier on 2015-10-02
Hello sudodus,

Thanks for your answer! I am not running, any graphical desktop on my final install, only text mode. Furthermore, I did not install anything custom, I simply followed the installer after having chosen "Command Line Install" from the initial menu.

The computer I am running this on is an old Lenovo. I will pretty much only edit text files on it.

---

### Post by sudodus on 2015-10-02
In that case I suggest that you re-install your system, this time connected via wire (ethernet) during the installation. Then the wired internet connection should continue to work after reboot. If you wish, you can also follow the instructions at the link in post #2, but it is probably not necessary.

At this early stage it is probably easier to re-install than to learn how to repair the internet connection.

---

### Post by ric_Poirier on 2015-10-02
sudodus,

Thanks, I will try this out and le you know,

Regards

---

### Post by ric_Poirier on 2015-10-02
Worked, problem solved,

Thanks sudodus!!

---

### Post by sudodus on 2015-10-03
I'm glad it works for you, and thanks for sharing the solution :KS

---

