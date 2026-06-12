---
title: "Problem with video card"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by Fewmurn on 2010-06-21
When i install my linux ubuntu 10.04 all was working fine.And the effects was working.I wasn't install the ati 9600 drivers.And i try to install them cuz i was wanting all to be fine  and ready so i can play gamez and have fun,but when i start install drivers i see that is too difficult but anyway i try to install drivers and i think i fail.After installing them effects wasn't working.Is there anyway i can delete all the drivers i have been installed ? please tell me so i can have back my effects and graphics been ready.Thank you

---

### Post by Mark Phelps on 2010-06-22
Had you checked here FIRST, you would have learned that there are no drivers for your ATI card and current Ubuntu versions and that by forcing the driver install, you not only hosed up your display, but created a lot of work for yourself ...

See the details in the link below about removing the fglrx drivers:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

Once you do that, reboot.  Ubuntu should then see your video card and install the open source drivers -- the only drivers that will work with your card and recent versions of Ubuntu.

---

### Post by Fewmurn on 2010-06-22
I try to delete.All effects work fine for me.But i still think i don't have a graphics drivers cuz i try to open a warcraft 3 game with wine programe (for opening exe files) and it doesn't run.It is possible that i don't use wine programe correctly but i think the problem is in drivers.And when i write this command 
sudo nano /etc/X11/xorg.conf it opens for me one window in which i don't know what
to do.Please help. that is the window [http://img145.imageshack.us/img145/9532/screenshotyy.png](http://img145.imageshack.us/img145/9532/screenshotyy.png)
(the picture is scrnshoot of my desktop) :confused:

---

### Post by Don Barzini on 2010-06-22
> **Fewmurn said:**
> I try to delete.All effects work fine for me.But i still think i don't have a graphics drivers cuz i try to open a warcraft 3 game with wine programe (for opening exe files) and it doesn't run.It is possible that i don't use wine programe correctly but i think the problem is in drivers.And when i write this command 
sudo nano /etc/X11/xorg.conf it opens for me one window in which i don't know what
to do.Please help. that is the window [http://img145.imageshack.us/img145/9532/screenshotyy.png](http://img145.imageshack.us/img145/9532/screenshotyy.png)
(the picture is scrnshoot of my desktop) :confused:

You don't have an xorg.conf file. Later versions of Xorg don't require an xorg.conf file. However, you could always create one if you think you need one.

For starters..... open your **/etc/default/grub** file as root and edit the following line......

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Add the term **nomodeset** to the end of the line within the quotes...

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

Then run **update-grub**

```
sudo update-grub
```

Reboot and check if video is O.K. If it needs more tweaking, you can create an xorg.conf file for yourself or try other KMS settings in the grub file.

More info here....

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)

---

