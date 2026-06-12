---
title: "Autostart programs at OS start up"
date: 2017-10-14
forum: Installation &amp; Upgrades
---

### Post by Tbuch on 2017-10-14
I'm just starting with the usual that I'm used to work in Windows.
Here, If you want to start an application when the OS starts, you just have to put the program in the "start folder"
What do you do in Ubuntu (more precisely Lubuntu)?

I would like the OS to start up with Thunderbird

---

### Post by Rex Bouwense on 2017-10-14
There is a GUI for that.  From the main menu chose Preferences->Default applications for LXsession.  Then select Autostart from the tabs on the left.  Add Thunderbird and close.  
Alternatively from the command line enter:
```
$ mkdir -p ~/.config/lxsession/Lubuntu/
$ touch ~/.config/lxsession/Lubuntu/autostart
$ leafpad autostart 
```

---

### Post by Tbuch on 2017-10-14
Thanks

---

