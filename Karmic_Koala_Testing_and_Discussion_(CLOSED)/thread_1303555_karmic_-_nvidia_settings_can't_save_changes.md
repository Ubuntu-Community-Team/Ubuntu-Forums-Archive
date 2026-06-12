---
title: "karmic - nvidia settings can't save changes"
date: 2009-10-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by powel212 on 2009-10-28
I want to add my second monitor in nVidia settings as I always used to in Jaunty by invoking

```
sudo /usr/bin/nvidia-settings
```

but when I try to save changes to xorg i get this error.

```
Failed to parse existing X config file '/etc/X11/xorg.conf'!
```

Any help is appreciated

Powel

---

### Post by gareththegeek on 2009-10-28
Have you tried backing up your xorg.conf then running
```
sudo nvidia-xconfig
```
to make a new one?

---

### Post by philinux on 2009-10-28
Please use gksudo for graphical apps.
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by powel212 on 2009-10-28
```
sudo nvidia-xconfig
```

That worked.

Thanks so much.

Powel

---

### Post by trulan on 2009-10-28
Yeah the problem occurs because there is no xorg.conf by default in Karmic.  You have to generate one before NVidia settings can parse it.  Also, NVidia settings most be run as root to properly save a configuration file.

There would obviously be a better way for nvidia-settings to handle these situations.  But since everything is going to automatic configuration, manual settings stuff will naturally be getting less and less attention...

---

### Post by bribera on 2009-10-28
Another alternative is to set the group of xorg.conf to "admin" and make it group writable. This allows you to use the menu link to the NVidia control panel as is.

---

### Post by Claus7 on 2009-10-28
Hello,

> **gareththegeek said:**
> Have you tried backing up your xorg.conf then running
```
sudo nvidia-xconfig
```
to make a new one?

I'll have that in mind in case I mess up my graphical environment. I do not know if this will work in my case, yet I was trying to find out a replacement to reconfigure easily xorg.conf file.

Regards!

---

### Post by powel212 on 2009-10-28
> Another alternative is to set the group of xorg.conf to "admin" and make it group writable. This allows you to use the menu link to the NVidia control panel as is.

This is a great idea. Can you give the details of how to "set the group of xorg.conf to "admin""? 

Not having to sudo the nvidia settings would be awesome.

P

---

### Post by onesojourner on 2009-10-29
has any one got a fix for this yet? I got rid of the error ```
 Failed to parse existing X config file '/etc/X11/xorg.conf'!
```

but I still can't get the setting to save.

---

### Post by bribera on 2009-10-29
Sure, although a caveat first:

Doing this grants your user (and all other admins) write access to a file that is normally protected from everyone but root. It's entirely possible that you will someday destroy your X settings by accident. When that day comes, use your backed-up copy ;)

The true solution is to make the NVidia control panel launcher be run through gksudo like other GUI programs that need access to sensitive information. I just haven't been able to figure out how to edit menu launchers in xubuntu yet :oops:

If you still want to change the file, follow along in your console:

```
brendan@pequod:~$ **ls /etc/X11/xorg.conf**
-rw-r--r-- 1 root root 0 2009-02-28 17:44 /etc/X11/xorg.conf
brendan@pequod:~$ **sudo cp /etc/X11/xorg.conf**
/etc/X11/xorg.conf.bak
[sudo] password for brendan:
brendan@pequod:~$ **sudo chgrp admin /etc/X11/xorg.conf**
brendan@pequod:~$ **sudo chmod g=rw /etc/X11/xorg.conf**
brendan@pequod:~$ **ls /etc/X11/xorg.conf**
-rw-rw-r-- 1 root admin 0 2009-02-28 17:44 /etc/X11/xorg.conf
```

That should allow you to use the menu launcher without trouble!

---

