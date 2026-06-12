---
title: "Video Card driver installation help"
date: 2006-08-13
forum: Installation &amp; Upgrades
---

### Post by linuxnoobie on 2006-08-13
I had to edit the xorg.conf file in /etc/x11 to properly change my resolution and keep the settings. While in there I noticed this section:

Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
Monitor "NEC FE991SB"
DefaultDepth 24
SubSection "Display"

Looks to me like my video card isn't recognized. It is an integrated video card, but its nVidia geforce 6100. So I went to nvidia.com. I don't know which driver I need.

This one?
[http://www.nvidia.com/object/linux_d..._1.0-8762.html](http://www.nvidia.com/object/linux_d..._1.0-8762.html)

Or this one?
[http://www.nvidia.com/object/linux_d..._1.0-5336.html](http://www.nvidia.com/object/linux_d..._1.0-5336.html)

I downloaded the first one but when I double click on it I get a weird message saying could not open gedit was has not been able to detect the character coding. Did I download the wrong file? Do I have to open it up via a different method? Someone please enlighten me.
Edit/Delete Message

---

### Post by Dr. Nick on 2006-08-13
That is because it is not executable, To make it executable right click it and hit properties, then check execute on the permissions tab. However that package can not be run from within a gui, you must shut down xorg and run it from a command line.

With ubuntu their is a better way to do it within the GUI, look here for the best ways to install the drivers,

I like method 1

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by linuxnoobie on 2006-08-13
Thanks.  I appreciate it.  This whole switching platforms is gonna take some time.

---

