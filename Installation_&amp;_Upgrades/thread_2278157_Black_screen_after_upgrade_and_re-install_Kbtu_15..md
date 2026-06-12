---
title: "Black screen after upgrade and re-install Kbtu 15.04"
date: 2015-05-14
forum: Installation &amp; Upgrades
---

### Post by Trad_dog on 2015-05-14
OS: Kubuntu 15.04
Video card: GTX 580
Screen configuration: Dual screen
Current driver: unsure. Most recommended commands to check are not working any more. 


I upgraded to Kubuntu 15.04 from 14.10 and got the usual black screen issue.
This time though  I did not manage to solve the issue in a reasonable time. I proceeded
to re-install from fresh. The live DVD system gets the configuration right but after
install I get the same issue again. 
Installing the latest Nvidia-346 driver did not help. 
I have uninstalled all nvidia drivers and tried to revert back to Nouveau, which worked
briefly. 

A lot seems to have changed with 15.04 and most posts on the web do not apply any more. 
gdm and lightdm are gone, replaced by sddm it seems. nvidia-xconfig is not a valid command
on my system and trying to apt-get install it does not work. 

Can someone help ?

---

### Post by entw on 2015-05-14
First things first you should always check the /var/log/Xorg.0.log```
grep EE /var/log/Xorg.0.log
```

And maybe switching back to lightdm will help. Don't forget to select lightdm. ```
sudo apt-get install lightdm-kde-greeter lightdm
```

---

### Post by Trad_dog on 2015-05-14
Hi entw, 

thanks for the reply. I decided to reinstall from scratch as the Nouveau was I think working initially. 
I'll revert back when it is finished. 

Best

---

### Post by Trad_dog on 2015-05-14
I reinstall the system and with nouveau, one of my screen works. There does not seem to 
be a lot of information on how to enter Dual Screen mode with xrandr or nouveau. Am I missing 
a reference ?

---

### Post by Trad_dog on 2015-05-14
rebooting a couple of times did the trick.

---

