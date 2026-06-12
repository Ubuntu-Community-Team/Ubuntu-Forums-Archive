---
title: "Login screen resolution too low"
date: 2008-09-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by SnowPunk98 on 2008-09-11
I just upgraded to 8.10 and almost all is well, however my login screen resolution is way too low, when I log in, it is fine. The login screen should be 1680x1050 can anyone advise?

---

### Post by hildebrand_us on 2008-09-11
You could try resetting the default resolution. Perhaps it was autodetected as a lower one for some reason.

sudo dpkg-reconfigure xserver-xorg
should show a menu for setting the X configuration you want.

---

### Post by Gina on 2008-09-11
You may need to install a driver from **System > Administration > Hardware Drivers.**  I had to do this for my nvidia graphics before I could get anything above 800x600.

---

### Post by stinger30au on 2008-09-11
this happens to me every now and then

when the log in screen start up and the resoltion is very low i hit CTRL + ALT + backspace and wait a few seconds while X reloads and it comes in at 1024x768 (my lcd monitor tells me so)

hope this helps

---

### Post by SnowPunk98 on 2008-09-11
When I log in the resolution is fine and I have the correct drivers installed. The only thing that is not correct is the login screen but after I log in everything is fine.

---

### Post by pastalavista on 2008-09-11
try..
```
sudo gedit /etc/usplash.conf
```

---

### Post by SnowPunk98 on 2008-09-12
It was set to 1024x768 and I changed it to 1680x1050 however it is still not correct.

---

### Post by philinux on 2008-09-12
> **hildebrand_us said:**
> You could try resetting the default resolution. Perhaps it was autodetected as a lower one for some reason.

**sudo dpkg-reconfigure xserver-xorg**
should show a menu for setting the X configuration you want.

That command does not set video options since 8.04 came out. Only keyboard and mouse now I'm afraid.

---

### Post by Xgen on 2008-09-12
When you edit usplash.conf  (xres=<value>  and yres=<value>) you need to:

sudo dpkg-reconfigure linux-image-`uname -r` 

to actually change the resolution.

---

### Post by philinux on 2008-09-12
A simple gui to change the login res is startupmanager available in synaptic, or with 
```
sudo apt-get install startupmanager
```

It appears in system>admin.

---

### Post by SnowPunk98 on 2008-09-16
> **Xgen said:**
> When you edit usplash.conf  (xres=<value>  and yres=<value>) you need to:

sudo dpkg-reconfigure linux-image-`uname -r` 

to actually change the resolution.

No dice

---

