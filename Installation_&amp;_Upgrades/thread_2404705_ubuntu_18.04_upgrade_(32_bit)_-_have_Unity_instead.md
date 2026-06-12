---
title: "ubuntu 18.04 upgrade (32 bit) - have Unity instead of Gnome"
date: 2018-10-27
forum: Installation &amp; Upgrades
---

### Post by Liamdale on 2018-10-27
I have an older 32 bit computer which had a dual boot Ubuntu 14.04/Windows xp.  I have recently upgrade the ubuntu 14.08 to 18.04.  All went well except that the unity 7.5 is the default GUI.  How can I switch (or install) the default Gnome GUI.

---

### Post by ajgreeny on 2018-10-27
You still have unity because you updated and unity was the DE of (14.08?) 14.04 or even 14.10.

The gnome desktop may be installed with this new gnome version of Ubuntu and you may be able to get to it from the login screen.

How did you update the system from 14.? to 18.04? It would not normally be a one activity upgrade as you move only one step at a time, eg, from 14.04 to 16.04 then from 16.04 to 18.04.

---

### Post by rob190 on 2018-10-27
I think you should have Gnome installed anyway but if not then 

sudo apt-get install gdm3

Then do:

sudo dpkg-reconfigure gdm3

I've just been through the same upgrade (i.e. 32 bit) which left me without a working desktop. I had to disable Wayland before it worked.

---

### Post by Liamdale on 2018-10-28
I upgraded directly from 14.04 using a usb flash drive.  I used the manual upgrade. I used the existing hard drive partitions (/ for system, /home for data, and existing swap partition)  During the installation it asked me to configure lightdm or gdm3.  Since it recommended lightdm ( I didn't what they were at the time) I chose lightdm.   

Research has shown me the difference between both display managers and I found how to reconfigure the display manager to gdm3.  I have confirmed using the command
```
 $ cat /etc/X11/default-display-manager
```

and the result is : /usr/sbin/gdm3

It seems that I am running gdm3 but unity is still displayed

---

### Post by Liamdale on 2018-10-28
I've done research on Wayland and found that it is a new 3d protocol to replace X11 protocol.  I found how to check which protocol is active on my computer.

```
echo $XDG_SESSION_TYPE
```

and the result is: X11

---

