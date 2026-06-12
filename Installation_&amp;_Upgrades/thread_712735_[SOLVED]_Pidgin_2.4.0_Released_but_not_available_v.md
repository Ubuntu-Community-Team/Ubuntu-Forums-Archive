---
title: "[SOLVED] Pidgin 2.4.0 Released but not available via via update manager"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by xcusmwah on 2008-03-02
I see that Pidgin 2.4.0 was just released but it is not available when I run the update manager.  

**Pidgin 2.4.0**
[http://digg.com/linux_unix/Pidgin_2_4_0_released_2](http://digg.com/linux_unix/Pidgin_2_4_0_released_2)

**I tried to Google how to update it and found the following article**
[http://www.kalpiknigam.com/blog/2007/12/18/latest-pidginrhythmbox-repository-for-ubuntu/](http://www.kalpiknigam.com/blog/2007/12/18/latest-pidginrhythmbox-repository-for-ubuntu/)

I was running an earlier version and by following those instructions it did update me but only to version 2.3.1.  Without having to download and compile it, is there a way to have it available in the update manager?  Thank you!

---

### Post by IanW on 2008-03-02
You'll have to wait for someone to package it for Ubuntu and upload it to the appropriate repository for Update Manager to find.

If you can't wait, download it from [http://www.getdeb.net/app/Pidgin]("http://www.getdeb.net/app/Pidgin") to your desktop & double-click the deb file.

---

### Post by zvacet on 2008-03-02
You can add getdeb as repository in your source list

```
gksudo gedit /etc/apt/sources.list
```

add line

deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/

save and close

```
sudo apt-get update
```

---

### Post by xcusmwah on 2008-03-02
Thank you, that worked perfectly.

---

