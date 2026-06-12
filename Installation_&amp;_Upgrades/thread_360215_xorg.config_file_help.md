---
title: "xorg.config file help"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by colyn on 2007-02-12
I have installed Ubuntu 6.10 on a custom built desktop computer with a Samsung SyncMaster 940MW LCD monitor. Everything seems to work fine except my screen res is not correct. It stretches the screen slightly horizontal and I need to set the res to 1440x900 which is the native res for this screen. I have located the information that needs to be copied into xorg.config but cannot access xorg.config.

Using a terminal I type sudo vi /etc/X11/xorg.config  (ENTER)
Password xxxxx  (ENTER)

I will then get...
~
~
~
~
~
"/etc/X11/xorg.config" [New File]

How do I access xorg.config to modify it?

---

### Post by invalid on 2007-02-12
The file is actually ```
/etc/X11/xorg.conf
```. This should help a bit.

---

### Post by colyn on 2007-02-12
> **invalid said:**
> The file is actually ```
/etc/X11/xorg.conf
```. This should help a bit.

Thanks

That's what I get for letting news group "experts" help me..

---

### Post by revoltism on 2007-02-13
could also test

```
sudo nano /etc/X11/xorg.conf
```


I like nano better....

---

### Post by invalid on 2007-02-13
> **colyn said:**
> Thanks

That's what I get for letting news group "experts" help me..

Haha, that was a good laugh :)

---

### Post by afd on 2007-02-13
[I've been having xorg.conf problems as well..]("http://ubuntuforums.org/showthread.php?p=2146901#post2146901")


any takers?

---

