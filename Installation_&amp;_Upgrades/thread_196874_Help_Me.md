---
title: "Help Me"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by jakeandgigi on 2006-06-14
i installed ubuntu on my puter and i got a black screen with white writting on it is says jake@jakeandgigi:~$ and i want to know what to do it asks me to type in a comand and i have no clue how to get to the desktop or anything form there  i could use the help:confused:

---

### Post by zxee on 2006-06-14
The fact that it didn't boot into a graphical desktop indicates something-probably that something either didn't install or that ubuntu had a problem with your hardware.
Please provide more specifics about your puter. You can try typing startx from the black screen you describe. Then copy the output and post it here-someone will try to help.

---

### Post by Sutekh on 2006-06-14
Did you try a server or expert install?  Which CD did you use? The LiveCD (Desktop CD) or the Install CD (Alternate CD)?
 
If you did a server install then you didn't install a desktop environment. You will now have to choose one to install. You can choose GNOME, KDE or XFCE, which are the desktop environments used in Ubuntu, Kubuntu and Xubuntu respectively.
 
If you want [GNOME]("http://www.gnome.org/") - Default Ubuntu Desktop, I'd use this command
 ```
sudo apt-get install ubuntu-desktop
```When prompted for a password, use your login one.
 
 If you want [KDE]("http://www.kde.org/") - Most Common Linux Desktop, I'd use
 ```
sudo apt-get install kubuntu-desktop
```If you want [XFCE]("http://xfce.org/") - very light desktop, I'd use
 ```
sudo apt-get install xubuntu-desktop
``` 
 These commands will install the respective desktop enironments with most of the basic programs you will need.

If you didn't do a server install, and things just went bad or weren't setup correctly, try using one of those commands anyway.

---

