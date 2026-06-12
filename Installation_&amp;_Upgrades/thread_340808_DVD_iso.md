---
title: "DVD iso"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by infinitezero on 2007-01-17
I know this is not the most brightest quesion and also a Kubuntu-ish question, but why the DVD iso and CDR iso. I take it the DVD has all the goodies.

Also, once I install Kubuntu can I also install gnome as well?

Thanks,
Rick

---

### Post by bruenig on 2007-01-17
The dvd iso has more stuff so that if you have a slow internet connection you can use it to get software off of instead of the online repositories. It doesn't install any more software by default though, you have to add it as a repo and then get the software off of it after it is installed.

You can get gnome afterwards by issuing
```
sudo apt-get install ubuntu-desktop
```
After issuing that you will be able to pick gnome or kde when you login.

---

### Post by infinitezero on 2007-01-17
Will it allow me to install more during the install or do I have to wait unit the install is finished?

Also, I have heard that there is no true root user, is this correct (I am a SuSe/Fedora refuge) or is there a way to enable it?

iz

---

### Post by spd106 on 2007-01-18
AFAIK you have to install the standard selection of packages first, then you can add more. It might be possible to select certain packages during install through expert mode, but this will be far slower than normal.

Ubuntu uses sudo to limit access to root powers, as this is generally safer than engaging root for a session. Least privilege etc. Root is disabled by default so If you want to enable it then just do **sudo passwd root** at a terminal.

---

### Post by infinitezero on 2007-01-18
Thanks for the info, I am going to install Kubuntu when I get home from work today.

iz

---

