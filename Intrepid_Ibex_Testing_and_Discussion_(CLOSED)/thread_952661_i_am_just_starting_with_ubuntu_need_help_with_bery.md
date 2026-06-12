---
title: "i am just starting with ubuntu need help with beryl"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jonlimle on 2008-10-19
i am new with ubuntu i am using 8.10 beta release and was wondering how to install beryl please help

---

### Post by OutOfReach on 2008-10-19
First of all, you shouldn't be using 8.10 beta as your main OS, because it is still under development and still contains bugs.

Second, Beryl is no more, it is now Compiz-Fusion. Compiz-Fusion is installed by default, to enable it goto System>Preferences>Appearance and to the Visual Effects tab. Then select either Normal or Extra, to turn it off select None
You can also enable extra effects by installing CCSM, goto a terminal (Applications>Accessories>Terminal) and type in:
```
sudo apt-get install compizconfig-settings-manager
```
Then when you want to enable more effects goto System>Preferences>Advanced Desktop Settings (or press Alt+F2 and type in ccsm).

---

### Post by Sam on 2008-10-19
It's no more beryl, it's compiz-fusion.


This said, does the 3d acceleration work ? In a terminal type:
```
glxinfo |grep rendering
```

If it says no, go to "System / Administration / Hardware Drivers" and make sure the graphic driver is enabled.


It is says yes, compiz should work. Go to "System / Preferences / Appearance", then "Visual Effects" tab.


To configure the effects, install the package [compizconfig-settings-manager](apt://compizconfig-settings-manager) then "System / Preferences / Advanced Desktop Effects Settings"

---

### Post by CloudFX on 2008-10-19
> **OutOfReach said:**
> First of all, you shouldn't be using 8.10 beta as your main OS, because it is still under development and still contains bugs.


At this point in the development release, using the Beta should be okay.

---

### Post by keep-on-smiling on 2008-10-19
Agreed - for a Beta this is remarkably stable - that said, you will get the odd bugs. 

I have experienced auto-closing CDrom trays, Pulseaudio is close to good, but might need a slight fiddle to have happy sounds, and nvidia install still kills jockey (tho the nvidia drivers are installed successfully).

The rest of the system is fine to my knowledge and at least you will have the latest Gnome, which is quite slick - OK so I like Tabs ! :)

---

