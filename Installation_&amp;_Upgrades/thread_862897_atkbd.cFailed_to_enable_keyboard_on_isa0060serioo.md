---
title: "atkbd.c:Failed to enable keyboard on isa0060/serioo"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by phantom308 on 2008-07-17
Hi ,
everything was working fine on my system Ubuntu .i was trying to make my mic work and i think i unistalled that alsa mixer now i rebooted and am not able to see my desktop.System reboots fine but only shows command line .i can login thru that .but NO DESKTOP/GUI ..i am in great trouble..Could anyone please please help me out with this..i tired reading several forums but no LUCK...

Awaiting response.
thanks.

---

### Post by Partyboi2 on 2008-07-18
maybe the ubuntu desktop was uninstalled, reinstall it by typing
```
sudo apt-get install gdm ubuntu-desktop
```

---

### Post by phantom308 on 2008-07-18
The box i am using for Linux has only USB support .whenever i run taht command it says enter the CD labeled Ubuntu .There is no cd-rom .only i can USB drive i can use .In that case how do i tell it to take that from USB ???

---

### Post by Partyboi2 on 2008-07-18
You probably need to make an adjustment to your sources.list
At the terminal type
```
sudo nano /etc/apt/sources.list
``` and at the top there should be a line that looks something like this
 ```
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
``` put a # in front of it, so it would look like this
```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted

``` then save the changes
Ctrl+o
enter
Ctrl+x
then type
```
sudo apt-get update
```
then
```
sudo apt-get install gdm ubuntu-desktop
```

---

### Post by phantom308 on 2008-07-18
I followed the steps .when i do apt-get update it mostly says Failed: ..............
then doing install gdm ubuntu-desktop..at the end says Unable to fetch some archives....what to try next ??

---

### Post by Partyboi2 on 2008-07-18
Are you hard wired to the internet and have a working connection?
Another thing to look at is to make sure that you have the repo's enabled in your sources.list
same thing as before except this time you want to remove the# from in front of the lines starting with deb except the cdrom line which you commented out before
So some thing like this
```
deb http://archive.ubuntu.com/ubuntu/ hardy main
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy restricted
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
```
then save
and 
```
sudo apt-get update
```
```
sudo apt-get install gdm ubuntu-desktop
```

---

