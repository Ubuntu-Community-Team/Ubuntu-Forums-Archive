---
title: "intel driver settings"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by mark9950 on 2010-02-21
Are there any settings to the ubuntu default video drivers?There are no performance vs. quality settings whatsoever so I can tweak my video.Do I have to download drivers from intel or what?Im a newbie.

---

### Post by RedSingularity on 2010-02-21
Can you post the output of 

cat /etc/X11/xorg.conf

So we can see you xorg file setup.

---

### Post by mark9950 on 2010-02-21
where is it?Im a newbie.

---

### Post by mark9950 on 2010-02-21
I found it,I think?

<!DOCTYPE busconfig PUBLIC
 "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
    <policy context="default">
        <allow own="org.x.config.display0"/>
        <allow send_destination="org.x.config.display0"/>
        <allow send_interface="org.x.config.display0"/>
        <allow own="org.x.config.display1"/>
        <allow send_destination="org.x.config.display1"/>
        <allow send_interface="org.x.config.display1"/>
    </policy>
</busconfig>



Looking for possible performance vs. quality settings.

---

### Post by RedSingularity on 2010-02-21
In a terminal type this

cat /etc/X11/xorg.conf

---

### Post by mark9950 on 2010-02-21
no such file or directory.

---

### Post by RedSingularity on 2010-02-21
Try running this first in terminal

 sudo Xorg  -configure

---

### Post by RedSingularity on 2010-02-21
Open a terminal window like this

CTL+ALT+F1

Then type in this command

sudo /etc/init.d/gdm stop

then......

 sudo Xorg  -configure

then..........

sudo /etc/init.d/gdm start

Then press CTL+ALT+F7

---

