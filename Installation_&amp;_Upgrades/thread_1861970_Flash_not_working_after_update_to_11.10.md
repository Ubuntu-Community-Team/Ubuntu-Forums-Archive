---
title: "Flash not working after update to 11.10"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by niceguy123 on 2011-10-16
Successful update from 11.04 to 11.10, but now flash plug in is missing in chrome browser. How do I get it back up and running? 

Thanks.

---

### Post by hoboy on 2011-10-16
I had the same problem I got this answer from the forum here that has solved my problem:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Uninstall the flash you have and go to the site you linked to and get the .tar.gz flash file. Right click it and extract here. Then put the resulting libflashplayer.so file into ~/.mozilla/plugins restart firefox if needed.

---

### Post by niceguy123 on 2011-10-16
> **hoboy said:**
> I had the same problem I got this answer from the forum here that has solved my problem:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Uninstall the flash you have and go to the site you linked to and get the .tar.gz flash file. Right click it and extract here. Then put the resulting libflashplayer.so file into ~/.mozilla/plugins restart firefox if needed.

Thanks,

How do I uninstall Flash in 11.10 ?

---

### Post by lovinglinux on 2011-10-16
> **niceguy123 said:**
> Thanks,

How do I uninstall Flash in 11.10 ?

If you followed those instructions, simply delete the file.

Perhaps will be easier for you to sue [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/), which I develop. It can remove conflicting plugins and install the latest version of flash or the one from the repositories. If you want to completely remove flash, use the advanced mode and select the option "Do not install". It will remove flash from several locations.

---

### Post by marco-stella2 on 2011-10-21
I also have the same problem but I am using Google Chrome and don't know exactly what I have to do. Could you help me, please? Where should I copy that file?

---

### Post by lovinglinux on 2011-10-21
> **marco-stella2 said:**
> I also have the same problem but I am using Google Chrome and don't know exactly what I have to do. Could you help me, please? Where should I copy that file?

Install [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) on Firefox, restart it, then execute the add-on Wizard from Flash-Aid menu in your Navigation toolbar. Open Chrome, type [noparse]about:plugins[/noparse] in the address bar, then click the "details" and disable the plugin that comes with Chrome (/opt/google/chrome/libgcflashplayer.so).

---

### Post by marco-stella2 on 2011-10-22
Thank you, but I still have a doubt. When I execute Flash-aid the terminal opens asking for the password but I cannot type anything in it...

---

### Post by lovinglinux on 2011-10-22
> **marco-stella2 said:**
> Thank you, but I still have a doubt. When I execute Flash-aid the terminal opens asking for the password but I cannot type anything in it...

That is normal. The terminal doesn't show your password for security reasons. Just type it and hit enter.

---

### Post by marco-stella2 on 2011-10-22
It must be some password I forgot because I cannot pass through this step. Is there any way to recover the password or to define a new one?

---

### Post by lovinglinux on 2011-10-22
> **marco-stella2 said:**
> It must be some password I forgot because I cannot pass through this step. Is there any way to recover the password or to define a new one?

It is the main password that you use to log on Ubuntu.

---

### Post by marco-stella2 on 2011-10-30
I had to reinstall Ubuntu and Flash-aid. Now everything works fine, thank you!

---

### Post by firefox834 on 2011-10-30
Re-install..oh no :confused: no way am i going through that again..ah well back to windows 7 only....bye troublesome Ubuntu :(

---

### Post by marco-stella2 on 2011-10-31
Well, my problem was that Flash-aid was going to delete some file and install another and to do this I needed the administrator password that I didn't remember. So I had to reinstall Ubuntu, but it has been very quick to do.

---

