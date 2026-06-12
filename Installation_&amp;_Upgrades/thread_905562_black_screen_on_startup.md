---
title: "black screen on startup"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by desolateone on 2008-08-30
Hi, i just recently installed ubuntu onto my older computer to try out.  I am incredibly new to linux, so im dont know what im doing.   the installation and everything works fine, and when i reboot its fine too.  but i installed the video drivers for my nvidia geforce 6200 and rebooted, like it wanted too.  Now when i rebooted, everything seemed fine until after the loading bar shows up, where the login is supposed to be.  Its just a black screen. :confused:  Can anyone help me fix this?
thanks

---

### Post by mrtomservo on 2008-08-30
I would suggest trying to install Envy or EnvyNG depending on what's available to you.  It will automatically install the proper drivers that you require.  You can find and install Envy by clicking on **System/Administration/Synaptic Package Manager**.  

Since it will be hard to click on what you need with a black screen you need to fix your xorg.conf file.  You can do this two ways.  Either way, when you boot and you get to the black screen...  Press the keys **CTRL-ALT-F1** this should kick you into a terminal login prompt.  Login.  You can either edit a text file or run a program that automates the task, it's up to you. First make a copy of your xorg.conf by typing:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.backup
```
This way we still have the original just in case.

Option 1 - reconfigure the package
```
sudo dpkg-reconfigure xserver-xorg
```
For the driver select either nv or vesa, but not nvidia.  All the other default options are probably fine.  

Option 2 - edit the config file by hand
You want to open up a config file and change where it says
Driver             "nvidia"
to
Driver             "nv"
To do this, type:
```
sudo nano /etc/X11/xorg.conf
```
And then save the file.

Try to restart your X windows manually.
To restart X windows type
```
sudo /etc/init.d/gdm restart
```

Let me know how it goes.

---

### Post by desolateone on 2008-08-30
ok i tried what you said, but neither worked.

Option 1
that worked at first.  But when i got the the keyboard options it gives me this:
xserver-xorg postinst warning: overwriting possibly-customized  configuration file; backup in /etc/X11/xorg.conf.20080830152240 then dumps me back to the terminal

Option 2 There is no driver "nvidia" in the file.
The only driver is "mouse"

---

### Post by xen-uno on 2008-08-30
Try this ...

[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

... best HowTo I've found to date

---

### Post by desolateone on 2008-08-30
sorry, didnt work.  i think it said it could not compile a nvidia kernel.

---

### Post by desolateone on 2008-08-31
ok sorry for the double post, but i've just formated the drive and reinstalled ubuntu, so how should i install it?

---

### Post by xen-uno on 2008-09-01
I would use the alternate CD myself (and I do as a rule). It can get around video problems until your in a position to do something about it. But since you've already installed off the Live CD (I assume), try the link I gave again and see if you get farther. If not, DL & burn the alternate, re-install, and see where you are.

---

