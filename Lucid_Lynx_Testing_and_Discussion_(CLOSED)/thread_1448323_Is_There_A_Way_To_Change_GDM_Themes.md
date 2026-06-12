---
title: "Is There A Way To Change GDM Themes?"
date: 2010-04-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jaco223 on 2010-04-06
Is there a way to change the GDM theme in lucid?

---

### Post by sisco311 on 2010-04-06
You can simply run the theme manager as user gdm:
```
sudo -u gdm dbus-launch gnome-appearance-properties
``` 

Or use this GUI tool:
[thread=1358026]GDM2 Configuration Tool[/thread]

Or 
[thread=1333683]HowTO: Comprehensive Guide to Customising GDM and XSplash[/thread]

For more information and advanced settings read [this]("http://library.gnome.org/admin/gdm/2.28/configuration.html.en").

---

### Post by bono8106 on 2010-04-08
After upgrade to Lucid Lynx (beta 1), to update the Login Screen (gdm) to  the new look, follow these steps:

1) run command shown in previous post
2) change Them to Ambiance and click Alt-U (customize button)
   - change Icons to LoginIcons
3) change the Background to Ubuntu (second-to-last image with purple-ish colors)

---

### Post by mc4man on 2010-04-10
> You can simply run the theme manager as user gdm:
Code:
sudo -u gdm dbus-launch gnome-appearance-properties

while I have no doubt it will work, probably a poor idea to run that that command while logged in, there could be some unintended behavior.
better to [log out before doing this]("http://ubuntuforums.org/showthread.php?p=9056501#post9056501"), though I guess you could go directly to appearance-properties rather than the control center ect.

---

### Post by sisco311 on 2010-04-10
> **mc4man said:**
> while I have no doubt it will work, probably a poor idea to run that that command while logged in, there could be some unintended behavior.
better to [log out before doing this]("http://ubuntuforums.org/showthread.php?p=9056501#post9056501"), though I guess you could go directly to appearance-properties rather than the control center ect.

Yes, you're right & I recommend your method to anyone, but I don't like to log out, so I tried another one. :)  

If I didn't miss something, all the processes started by running gnome-control-center are terminated after the nested X server is closed: 

```
Xnest -ac :13.0&
DISPLAY=:13.0 gnome-terminal

```

in the new X:
```
xhost SI:localuser:gdm
sudo HOME=/var/lib/gdm -u gdm gnome-control-center
```

---

### Post by Crunchy the Headcrab on 2010-04-10
Also, the ugly purple background is in:
/usr/share/backgrounds/warty-final-ubuntu.png

So it's as easy as copying/moving an image named the same thing to that location to change the background.

---

### Post by mc4man on 2010-04-10
>  I don't like to log out, so I tried another one
A little fooling around suggests probably not a big deal either way (though I guess I'd prefer to log out.

Anyway on a tester (dual boot lucid - nvidia-current, nouveau), running while logged in would always initially add 2 accessibility icons - one by itself, one to indicator applet.
A logout would remove the stand alone, though the one in the applet would remain.

Turns out that at least here the file %gconf.xml in ~/.gconf/desktop/gnome/accessibility/keyboard was being rewritten to this on the last line

<entry name="enable" mtime="1268541481" type="bool" value="true"/>

( some other 'oddities' on one install I now think weren't related to running comm. while logged in, though possibily to trying to remove the icon before finding what was causing it's appearance

---

### Post by hourna on 2010-04-10
i have installed GDM2 Configuration Tool but now, appearance preferences window pops-up and asks me to choose a theme just before the login screen comes up. this is really weird. i close the windows and then i can enter my password and login. i removed GDM2 Configuration Tool but the pop-up window is still there. 

now, i just want to revert to the default one.

---

