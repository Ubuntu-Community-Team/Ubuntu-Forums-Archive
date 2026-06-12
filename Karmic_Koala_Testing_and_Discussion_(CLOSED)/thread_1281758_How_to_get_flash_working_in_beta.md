---
title: "How to get flash working in beta?"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bridgetothesun on 2009-10-03
I have been upgrading since Alpha 6 and I'm on Beta now. How do get flash working? I haven't got it to work since Alpha 6. I tried gnash and swfdec but there were issues with both. What is the most foolproof way to get it to work?

I'm a newbie to linux.

---

### Post by psyke83 on 2009-10-03
Adobe Flash exists for Linux as well. Remove any gnash or swfdec plugins, and install the package "flashplugin-installer".

If you have problems, [this]("http://ubuntuforums.org/showpost.php?p=8017411&postcount=21") post goes into detail how to remove all flash plugins.

---

### Post by stephana on 2009-10-03
if you're using firefox, just put the libflashplayer.so into ~/.mozilla/plugins/

if the /plugins folder there, you can create it by your own :)

you can get the libflashplayer.so directly from the Adobe Website


greetz from germany, stephana

---

### Post by Hreinsi on 2009-10-03
I just install ubuntu restrigted extras works fine

---

### Post by psyke83 on 2009-10-03
> **stephana said:**
> if you're using firefox, just put the libflashplayer.so into ~/.mozilla/plugins/

if the /plugins folder there, you can create it by your own :)

you can get the libflashplayer.so directly from the Adobe Website


greetz from germany, stephana

Please, **do not** follow those instructions. You should always use the packaging system when possible, or you will be **guaranteed** to experience difficulties in the future.

Installing stephana's way will cause the Flash plugin to never update, and possibly conflict with future installs of the Flash plugin.

Installing from the .deb package (flashplugin-installer) will allow easy (un)installation and updates from the official repositories.

```
$ sudo apt-get install flashplugin-installer
```

---

### Post by stephana on 2009-10-03
psyke83 you're right...but for me it was the better solution to put the libflashplayer.so from the Adobe Website direktly in the plugins folder of my browser, because i'm working on a 64-Bit Ubuntu, an my experience with the flashplugin-installer where not so good(not working correctly some times). 

stephana

---

### Post by FrancoNero on 2009-10-03
downloaded the flash 10 64bit alpha from adobe and it works fine. the usualy problems of my laptop overheating in full-screen flash are normal, have the same problems with 32bit as well..

---

