---
title: "Screen Resolution gone after upgrade"
date: 2012-05-02
forum: Installation &amp; Upgrades
---

### Post by dhirajkhanna on 2012-05-02
Hi All,
Upgraded to Ubuntu 12.04 and my display resolution has gone bad. The monitor is an Acer AL1702W. xrandr output is as shown :-
```
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2048 x 2048
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
   1440x990_60.00   60.0  
```

The last entry was added by the following code :-

```
xrandr --newmode "1440x990_60.00"  118.25  1440 1528 1680 1920  990 993 1003 1027 -hsync +vsync

xrandr --addmode VGA1 1440x990_60.00
```

This I made into a shell script and now when I run it, I get the following :-

```
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  20
  Current serial number in output stream:  20

```

Need some help here please. Thanks.

---

### Post by dino99 on 2012-05-02
rename or remove xorg.conf as now the kernel directly deal with X, and reboot. Then check the grahic driver activation (sudo jockey-gtk , if you are using gnome of course)

---

### Post by dhirajkhanna on 2012-05-02
Don't have an xorg.conf

This is when I locate xorg.conf

```
/usr/share/X11/xorg.conf.d
/usr/share/X11/xorg.conf.d/10-evdev.conf
/usr/share/X11/xorg.conf.d/11-evdev-quirks.conf
/usr/share/X11/xorg.conf.d/11-evdev-trackpoint.conf
/usr/share/X11/xorg.conf.d/50-synaptics.conf
/usr/share/X11/xorg.conf.d/50-vmmouse.conf
/usr/share/X11/xorg.conf.d/50-wacom.conf
/usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf
/usr/share/man/man5/xorg.conf.5.gz
/usr/share/man/man5/xorg.conf.d.5.gz

```

---

### Post by dhirajkhanna on 2012-05-02
This is the output for sudo jockey -gtk

```
Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed

(jockey-gtk:8910): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed

```

---

