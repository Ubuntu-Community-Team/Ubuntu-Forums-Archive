---
title: "Gnome 2.27.1"
date: 2009-05-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-05-05
According to the gnome schedule our first gnome build should be coming shortly:

 May 6 GNOME 2.27.1 unstable release

Looks to be stuff all changes though - some bug fixes, translation updates.

---

### Post by Neon Lights on 2009-05-06
Yup, Phoronix has an article on it [here]("http://www.phoronix.com/scan.php?page=news_item&px=NzI0Ng"). Looking forward to the Cheese improvements and seeing what's changed in EOG. =]

---

### Post by jmmL on 2009-05-06
I'm really interested in the new cheese features as well. I'm trying to build it from source, but when I run ./configure I get :```

checking for CHEESE... configure: error: Package requirements (  glib-2.0 >= 2.16.0   gobject-2.0 >= 2.12.0   gio-2.0 >= 2.16.0   gtk+-2.0 >= 2.16.0   gdk-2.0 >= 2.14.0   gnome-desktop-2.0 >= 2.25.1   gconf-2.0 >= 2.16.0   gstreamer-0.10 >= 0.10.20   gstreamer-plugins-base-0.10 >= 0.10.20   libebook-1.2 >= 1.12.0   cairo >= 1.4.0   dbus-1 >= 1.0   dbus-glib-1 >= 0.7   hal >= 0.5.9   pangocairo >= 1.18.0   librsvg-2.0 >= 2.18.0) were not met:

No package 'gtk+-2.0' found
No package 'gdk-2.0' found
No package 'gnome-desktop-2.0' found
No package 'gconf-2.0' found
No package 'gstreamer-0.10' found
No package 'gstreamer-plugins-base-0.10' found
No package 'libebook-1.2' found
No package 'cairo' found
No package 'dbus-glib-1' found
No package 'hal' found
No package 'pangocairo' found
No package 'librsvg-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables CHEESE_CFLAGS
and CHEESE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I'm not really sure what to do here, I haven't built that many packages before. All the packages it complains about not having are installed.

---

### Post by JohnJackson on 2009-05-06
Are the development packages installed?

---

### Post by jmmL on 2009-05-06
> **JohnJackson said:**
> Are the development packages installed?
D'oh!
Thanks, installs fine now.

---

### Post by JohnJackson on 2009-05-06
No problem, I forget that too sometimes

---

### Post by gjoellee on 2009-05-06
The Ubutnu devleopers are probably building all the GNOME packages, so we should see GNOME 2.27.1 soon in Karmic.

---

### Post by plun on 2009-05-11
Broken directly.....  Warning !!!

```
The following packages will be REMOVED:
  deskbar-applet dockbar gnome-media gnome-volume-control-pulse libgnome-media0
  python-gnome2-desktop python-gnome2-extras rhythmbox screenlets sound-juicer ubuntu-desktop
```

It seems to be gnome-media 2.27.1 which is broken.


8)

---

### Post by Starks on 2009-05-11
2.27.1 packages are starting to slowly land.

No conflicts yet.

---

### Post by plun on 2009-05-11
> **Starks said:**
> 2.27.1 packages are starting to slowly land.

No conflicts yet.

I have a mess.....

```
The following packages will be REMOVED:
  gnome-games nautilus
The following packages have been kept back:
  python-gobject-dev ubiquity-ubuntu-artwork
The following packages will be upgraded:
  gnome-cards-data gnome-games-data hal lib32ncurses5 libhal-dev libhal-storage1 libhal1
  libncurses5 libncurses5-dev libncursesw5 nautilus-data ncurses-bin

```

The hal error described within another thread is a "grave-bug".....

So I just wait.....;)

---

### Post by super.rad on 2009-05-11
yeah it's telling me it needs to remove gnome-games, nautilus and ubuntu-desktop. already installed the hal upgrade, just have to wait it out now

---

### Post by Starks on 2009-05-11
apt hasn't asked me to remove anything yet.

---

### Post by plun on 2009-05-12
Fixed today and 2.27.1 is rolling in....:)

---

### Post by davideotape on 2009-05-12
The updates seem to be coming in slowly but surely now :D

---

