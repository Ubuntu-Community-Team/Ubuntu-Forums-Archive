---
title: "Ubuntu 7.07"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by jatrojoomla on 2007-09-15
Hi all U users!
I am very new at ubuntu. 
Now I have Ubuntu 7.04 which I downloaded from:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)


I saw some one recommended ubuntu 7.07 for skype use, 
[http://forum.skype.com/index.php?showtopic=96497](http://forum.skype.com/index.php?showtopic=96497)

**_Plz any one send me the link for download ubuntu 7.07_**    

Thanks

---

### Post by lisati on 2007-09-15
the "7.07" could be a typo - there isn't one! 7.04 should be fine.

---

### Post by jatrojoomla on 2007-09-15
Thanks for reply.
is that possible to install skype on ubuntu & how? I had try ed but failed.

---

### Post by lisati on 2007-09-15
I went to the skype website @ [www.skype.com](www.skype.com), clicked on the word "download" on the menu (**Not** the "download now" button), chose the version for Ubuntu, and followed the instructions that the good folks at skype provided.

---

### Post by jatrojoomla on 2007-09-15
Thanks!
I also went to [http://www.skype.com/intl/en/download/skype/linux/](http://www.skype.com/intl/en/download/skype/linux/)
download skype-debian_1.4.0.99-1_i386.deb from [Feisty Fawn (7.04) link]


enter command:

---------------------------------------------------------------------------------------------------
fuelchat@fuelchat:~$ pwd
/home/fuelchat

fuelchat@fuelchat:~$ ls
Desktop  Examples

fuelchat@fuelchat:~$ cd Desktop/

fuelchat@fuelchat:~/Desktop$ ls
skype-debian_1.4.0.99-1_i386.deb

fuelchat@fuelchat:~/Desktop$ sudo dpkg -i --force-architecture skype-debian_1.4.0.99-1_i386.deb Password:
Selecting previously deselected package skype.
(Reading database ... 88003 files and directories currently installed.)
Unpacking skype (from skype-debian_1.4.0.99-1_i386.deb) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libqt4-core (>= 4.2.1); however:
  Package libqt4-core is not installed.
 skype depends on libqt4-gui (>= 4.2.1); however:
  Package libqt4-gui is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype

fuelchat@fuelchat:~/Desktop$ 
-----------------------------------------------------------------------------------

**_showing error_**

---

### Post by lisati on 2007-09-15
Hmmmm... I'm not sure..... I didn't have that trouble when I installed skype. Anyone else?

---

### Post by K.Mandla on 2007-09-15
Try 

```
sudo apt-get install -f
```
which should draw in the needed packages from the repositories. If they're accessible, that is.

---

### Post by jatrojoomla on 2007-09-15
AFTER sudo apt-get install -f



joomla@joomla:~/Desktop$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  libqt4-gui skype
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 26.3MB disk space will be freed.
Do you want to continue [Y/n]?

---

### Post by ludavicious on 2007-09-15
Hi. I don't have any problems with Skype in Feisty Fawn. I just downloaded the deb package from skype webpage and right clicked on downloaded deb file a choose "Install with GDebi" (or something like that ) from menu. Skype was installed automatically and some additional libraries as well ( one of them was " libqt4-gui " mentionted above). 

Have you tried to install libraries libqt4-core and libqt4-gui  manually via Synaptic or apt before you install Skype? (Stupid question (sugestion) I know, but it's worth of try.)  Try in terminal: 
```
sudo apt-get install libqt4-core
sudo apt-get install libqt4-gui

```

---

### Post by trippinnik on 2007-09-15
if you add the repo to your sources.list (in the /etc/apt/ directory) you can install using apt-get or aptitude.  You'll get updates with the rest of your packages and dependancies will also be dealt with.

---

### Post by jnorthr on 2007-09-15
Thank you very much for that link. I've just installed it on ubuntu 7.0.4 and skype even works across my wireless connect to my xp desktop onto the net 8-) 

I have skype on my desktop but i don't think it was used other than the user profile which i'm using on my lap.

I do have sound problems and my microphone won't record but i think this is an alsa sound issue.  The only mistake i made was to close skype which does not leave any icon on the desktop but there are several skype processes running in the background that we can only see by going to system>administration>System Monitor and manually ending the skype processes there. I could then log back into skype normally. When Skype runs on my XP machine, there is a small skype icon in the tray showing me it's still active, but i don't know how to achieve the same on ubuntu. Othrwise,
it rocks:guitar:

---

### Post by maybeway36 on 2007-09-15
Why is this a poll, and what's Ubuntu 7.07?

---

### Post by ludavicious on 2007-09-16
> **jnorthr said:**
> When Skype runs on my XP machine, there is a small skype icon in the tray showing me it's still active, but i don't know how to achieve the same on ubuntu.

I have skype icon on my system tray bar since Skype was firstly runned.  I was searching in all menus in Skype, but had no luck to find any switch or option how to enable/disable icon in "systray".  
There's atachment with image of my systray with skype icon. I have only one idea how to enable it - try to reinstall Skype.

> **maybeway36 said:**
> Why is this a poll, and what's Ubuntu 7.07? Ubuntu 7.07 is just a typographical mistake, see first two posts in this topic.

---

