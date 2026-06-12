---
title: "Synaptic Package Manager not allowing to add Repositories"
date: 2015-07-16
forum: Installation &amp; Upgrades
---

### Post by V_Narayanan on 2015-07-16
Hi
As I am unable to add repositories graphically, I used the command  "gksu --desktop /usr/share/applications/software-properties-gtk.desktop  /usr/bin/software-properties-gtk" and got the below results.

Please tell me, what I should do

The Terminal Output is pasted below
Yours
VN

[EMAIL="root@Lenovo-B490:/etc/apt/apt.conf"]root@Lenovo-B490:/etc/apt/apt.conf[/EMAIL].d#  gksu --desktop /usr/share/applications/software-properties-gtk.desktop  /usr/bin/software-properties-gtk
/usr/share/themes/MBuntu-Y-For-Gnome-Fallback/gtk-2.0/widgets/panel.rc:18:  Unable to locate image file in pixmap_path:  "images/panel/panel-normal.svg"
/usr/share/themes/MBuntu-Y-For-Gnome-Fallback/gtk-2.0/widgets/panel.rc:21: Background image options specified without filename
/usr/share/themes/MBuntu-Y-For-Gnome-Fallback/gtk-2.0/widgets/panel.rc:27:  Unable to locate image file in pixmap_path:  "images/panel/panel-active.svg"
/usr/share/themes/MBuntu-Y-For-Gnome-Fallback/gtk-2.0/widgets/panel.rc:30: Background image options specified without filename
/usr/share/themes/MBuntu-Y-For-Gnome-Fallback/gtk-2.0/widgets/panel.rc:61:  error: invalid string constant "button", expected valid string constant
Gtk-Message: Failed to load module "canberra-gtk-module"

(gksu:4948): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did  not receive a reply. Possible causes include: the remote application  did not send a reply, the message bus security policy blocked the reply,  the reply timeout expired, or the network connection was broken.
GConf Error: No D-BUS daemon running


(gksu:4948): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did  not receive a reply. Possible causes include: the remote application  did not send a reply, the message bus security policy blocked the reply,  the reply timeout expired, or the network connection was broken.
GConf Error: No D-BUS daemon running


(gksu:4948): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did  not receive a reply. Possible causes include: the remote application  did not send a reply, the message bus security policy blocked the reply,  the reply timeout expired, or the network connection was broken.
GConf Error: No D-BUS daemon running


(gksu:4948): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did  not receive a reply. Possible causes include: the remote application  did not send a reply, the message bus security policy blocked the reply,  the reply timeout expired, or the network connection was broken.
GConf Error: No D-BUS daemon running


(gksu:4948): GConf-CRITICAL **: gconf_value_free: assertion 'value != NULL' failed
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 101, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 98, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 109, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 599, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python3/dist-packages/aptsources/distro.py", line 89, in get_sources
    (self.id, self.codename))
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template for Ubuntu/n/a
[EMAIL="root@Lenovo-B490:/etc/apt/apt.conf"]root@Lenovo-B490:/etc/apt/apt.conf[/EMAIL].d#

---

### Post by v3.xx on 2015-07-16
What happens if you just enter
```
software-properties-gtk
```
?

---

