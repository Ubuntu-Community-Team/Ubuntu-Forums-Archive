---
title: "Adding new screensavers in Lucid Lynx"
date: 2010-04-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Metallion on 2010-04-06
Hi all

Since today I've decided to try out the beta of Lucid Lynx. One problem I'm encountering is an inability to add new screensavers. I've started by looking for the .desktop files of the existing screensavers which seem to be in **/usr/share/applications/screensavers**

Then I copied the personal-slideshow.desktop file and edited it to make my own customized slideshow screensaver. I changed the name and comment lines inside after which it always used to show up in gnome's screensavers dialog but now it doesn't. I tried using gconf-editor to manually set it but still nothing.

Does anyone know what might be the causes of this? This had also started happening in my Arch lately so I'm guessing that the latest version of gnome-screensavers requires some kind of trigger to update its database. I'll post the contents of my custom .desktop just in case.

```
[Desktop Entry]
Name=Metallion slideshow
Comment=kakkendrol
Exec=/usr/lib/gnome-screensaver/gnome-screensaver/slideshow --location=/home/metallion/.scrnsvr
TryExec=/usr/lib/gnome-screensaver/gnome-screensaver/slideshow
StartupNotify=false
Terminal=false
Type=Application
Categories=GNOME;Screensaver;
OnlyShowIn=GNOME;
X-Ubuntu-Gettext-Domain=gnome-screensaver
```

---

