---
title: "How to repair kde - ubuntu - 12.04 lts"
date: 2013-04-03
forum: Installation &amp; Upgrades
---

### Post by Ashi Gupta on 2013-04-03
Hello everyone,

I am new to ubuntu and working with it is wonderful. I installed 12.04 kde in my laptop. To change kde to gnome i used "apt-get install gnome" command for gnome installation. After complete installation it asked me to select option between gdm and lightgdm. I selected lightgdm but after that i am not able to open neither kde nor gnome. But i am able to start virtual terminal tty1 using Alt+F1. 

Now i don't know how to repair this. Please tell me how to repair my system to get back at-least kde which i installed. I am using UBUNTU 12.04 LTS.

Thank you.

Regards,
Ashi

---

### Post by ibjsb4 on 2013-04-03
If your not able to log into anything how are you getting to tty?

Try the command **startx** see if it will do anything.

You are trying to access the different desktops at login?  What choices (desktops) do you have?

---

### Post by Ashi Gupta on 2013-04-03
I am able to start ubuntu but then after a blank screen is coming. At that moment i giving Alt+f1 and then i am getting tty terminal. I have no desktop choices. I tried startx from tty terminal but it is also not working.

---

### Post by ibjsb4 on 2013-04-03
So at login you cannot click on the icon and choose a desktop.

[ATTACH=CONFIG]240910[/ATTACH]

We need something to go on, like an error report.

```
sudo apt-get -f install
```

Any errors from that?

---

### Post by Cheesemill on 2013-04-03
You could try switching your display manager to gdm...
```
sudo dpkg-reconfigure gdm
```

---

### Post by oldschoolgentoo on 2013-04-03
impression i am getting from  OP is  X is not configured.

---

### Post by Ashi Gupta on 2013-04-04
sudo apt-get -f install
sudo dpkg-reconfigure gdm

These commands are not working. I able to get the tty terminal from filesafe mode not from the normal mode. After applying these commands i am getting error " FATAL ERROR : NO SCREENS FOUND".

Any suggestions....

Ashi

---

### Post by ibjsb4 on 2013-04-04
Ok, lets try oldschoolgentoo's suggestion.

```
sudo dpkg-reconfigure xserver-xorg

sudo service lightdm start
```

I wonder if your options may of been changed.  Were you using nomodeset?

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

[http://www.kubuntuforums.net/showthread.php?58849-Kubuntu-12-04-LTS-64-bit-Black-Screen-with-Intel-Based-Laptop](http://www.kubuntuforums.net/showthread.php?58849-Kubuntu-12-04-LTS-64-bit-Black-Screen-with-Intel-Based-Laptop)

---

