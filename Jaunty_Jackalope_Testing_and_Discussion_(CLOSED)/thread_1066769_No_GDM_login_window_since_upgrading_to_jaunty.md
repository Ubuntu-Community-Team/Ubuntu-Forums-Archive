---
title: "No GDM login window since upgrading to jaunty"
date: 2009-02-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by n3had on 2009-02-11
HI everyone, this is my first post. Its been around a year since i switched to linux. Whenever i find my ubuntu 'bugged' i do my best to search more info about the bug(on this forum) and rectify it myself. Unfortunately today i have failed miseably.. So i had to register to post about this bug and forgive me if there are threads on the same topic.

1. Everything was fine till yesterday as i was logged on Intrepid Ibex 64 bit. I was looking forward to give jaunty a try so i did this

2. sudo update-manager -d. It took a good deal of time and needed restart(compiz is enabled)

3. After the boot process and nvidia logo, the system came to a abrupt halt with a loading cursor animation. I waited for some time.. 

so i decided to look into the terminal.. pressed ctrl+alt+f1 and i got something similar to this...

(i don't know how to dump the text fromm tty1/7)

kinit: name_to_dev_t(/dev/disk/by-uuid/5e3234bd-e136-49b5-b97c-663caddc0481) = sda2(8,2)
kinit: trying to resume from /dev/disk/by-uuid/5e3234bd-e136-49b5-b97c-663caddc0481
kinit: no resume image, doing normal boot...

the kernel is 2.6.27-11

so i've to.. 

4. ```
sudo /etc/init.d/gdm stop
         startx
```

5. Switch to tty7 where the xsession starts and i can use some applications like firefox pidgin, and yes compiz works fine as i can check the animations on some of the screenlets.

6. So i removed nVidia restricted drivers.. Jaunty repo 180.27 and installed the STABLE release 180.29 from nVidia

But i am still stuck with the same issue... 

I have attached the xorg.conf and log file below 

Any help would be appreciated.

---

### Post by Archmage on 2009-02-11
Yes, the closed driver of Nvidia isn't ready for Jaunty. It should work in the Beta-Version. No need to report this bug. Turn of the restricted driver and start hunting for undiscoverd bugs.

---

### Post by meborc on 2009-02-11
upgrading to alpha is not always painless... if you really want to test jaunty alpha, i would do a reinstall

the upgrading testing starts in RC phase, where all the major upgrades have already happened... sorry to hear your system got bogged

---

### Post by n3had on 2009-02-11
> **Archmage said:**
> Yes, the closed driver of Nvidia isn't ready for Jaunty. It should work in the Beta-Version. No need to report this bug. Turn of the restricted driver and start hunting for undiscoverd bugs.

I've already purged the restricted drivers and using the one from nvidia website.. 

thanks for the response.. 

P.S. KDE and QT applications seems to work fine. Its just the Gnome desktop that doesn't respond

---

### Post by cariboo on 2009-02-11
You haven't completed your upgrade, the current kernel is 2.6.27-20, I would suggest running:

```
sudo apt-get install -f
```

to make sure there aren't any missing dependencies, then:

```
sudo apt-get update && sudo apt-get upgrade
```

Jim

---

### Post by n3had on 2009-02-11
> **cariboo907 said:**
> You haven't completed your upgrade, the current kernel is 2.6.27-20, I would suggest running:

```
sudo apt-get install -f
```

to make sure there aren't any missing dependencies, then:

```
sudo apt-get update && sudo apt-get upgrade
```

Jim

Thank you for the response. sudo apt-get upgrade did fetch around 70 files for upgradation.So after a quick reboot the terminal still shows 2.6.27-11 generic..


EDIT: I've installed the latest kernel 2.6.28-7-server manually as in this 

[http://ubuntuforums.org/showpost.php?p=6717324&postcount=3](http://ubuntuforums.org/showpost.php?p=6717324&postcount=3) and problem with startx still persists.. still no gnome desktop nor login window..

EDIT 2: Had issues with /etc/apt/sources.list i had to seperate the lines and after that some more packages got updated.. and i still have to stop GNOME DISPLAY MANAGER everytime.

---

### Post by n3had on 2009-02-12
Exact same issue [here]("http://ubuntuforums.org/showpost.php?p=6240852&postcount=1")

---

### Post by n3had on 2009-02-12
After trying ```
sudo dpkg --configure -a
```
It seems ubuntu-desktop is not configured properly which depends on gnome-session-canberra which is not installed and i get the below error when i try to install it..


```
Selecting previously deselected package gnome-session-canberra.
Unpacking gnome-session-canberra (from
.../gnome-session-canberra_0.11-1ubuntu1_all.deb) ...
dpkg: error processing
/var/cache/apt/archives/gnome-session-canberra_0.11-1ubuntu1_all.deb
(--unpack):
 trying to overwrite
`/usr/share/gnome/autostart/libcanberra-login-sound.desktop', which is also
in package libcanberra-gnome
```

Causes ubuntu-desktop to remain broken with unmet dependencies.

UPDATE: GDM working! sudo apt-get dist-upgrade fixed the whole system because system was partially upgraded.

---

### Post by n3had on 2009-02-12
Can someone mark the title [SOLVED]

thankyou,

nehad

---

