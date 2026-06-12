---
title: "QT Appearance Preferences?"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by fraser_m on 2009-10-03
In jaunty, there used to be an Appearance Preferences for QT, in Gnome. It had various different settings for changing fonts and themes for QT apps, but doesn't seem to be there any more. Does anybody know where it went / how to get it back?

---

### Post by ceramicm on 2009-10-03
For Qt4: ```
sudo apt-get install qt4-qtconfig
```

For Qt3: ```
sudo apt-get install qt3-qtconfig
```

I think qtconfig is what you want--"The Qt Configuration program allows end users to configure the look and behavior of any Qt 4 application." 

You shouldn't need this though...Newer versions of Qt automatically integrate into GNOME using native GTK rendering through QGTKStyle.

Edit: These will only work for pure Qt apps, not KDE apps. Post again if you need help with those.

---

### Post by rubinstein on 2009-10-03
I can't seem to find a setting to change the antialiasing settings. Qt4 apps have ugly fonts, whereas all the other gtk apps have nice fonts in my Karmic Ubuntu test installation.

Do I have to install some other KDE config package?

---

### Post by ceramicm on 2009-10-03
Which apps specifically are you having problems with?

---

### Post by rubinstein on 2009-10-04
> **ceramicm said:**
> Which apps specifically are you having problems with?

VirtualBox OSE and ScribusNG, which use the qt4 toolkit.

---

### Post by ceramicm on 2009-10-07
(Sorry, forgot about this thread.)

I have installed Virtualbox OSE in the past, and it has always appeared the same as my other applications, with GTK+ controls and my system fonts. No KDE packages should be necessary for it to theme correctly, because it is a QT application and not part of KDE.

If fonts are your biggest problem, you might try creating a ~/.fonts.conf file. All applications (KDE, QT, GTK+, GNOME, etc.) will use settings from that file (I think) if it exists. To create the file, just use: ```
gedit ~/.fonts.conf
```

Here is a sample to get you started:
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="autohint" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>none</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>false</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintnone</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>

```

---

### Post by rubinstein on 2009-10-09
Thanks ceramicm, experimenting with ~/.fonts.conf did the trick.

---

