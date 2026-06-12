---
title: "New Karmic GDM"
date: 2009-08-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by optimistique1 on 2009-08-11
Hello All

I know that this is less of a technical/bug reporting query but I was wondering if anyone knows how to set the New Karmic GDM background so that it is the same wallpaper as the Desktop?
Many thanks
Garry

---

### Post by wayne_cat on 2009-08-11
> **optimistique1 said:**
> Hello All

I know that this is less of a technical/bug reporting query but I was wondering if anyone knows how to set the New Karmic GDM background so that it is the same wallpaper as the Desktop?
Many thanks
Garry


[http://ubuntuforums.org/showpost.php?p=7576112&postcount=365](http://ubuntuforums.org/showpost.php?p=7576112&postcount=365)

---

### Post by optimistique1 on 2009-08-11
Cool, Thank you!:P

---

### Post by soapytheclown on 2009-08-11
out of interest ive had a gdm update for a week or so now ive got version 2.20.10-0-Ubuntu3 installed and 2.27.4.0ubuntu9 is available, however whenever i sudo aptitude safe-upgrade it along with 34 other packages are held back, does anyone know if its safe to do a full-upgrade? the packages held are:

The following packages have been kept back:
  devicekit-power f-spot gdm gnome-power-manager libmono-corlib2.0-cil 
  libmono-data-tds2.0-cil libmono-data2.0-cil libmono-getoptions2.0-cil 
  libmono-posix2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil 
  libmono-sqlite2.0-cil libmono-system-data2.0-cil 
  libmono-system-web2.0-cil libmono-system2.0-cil libmono2.0-cil 
  libpulse-browse0 libpulse-mainloop-glib0{a} libpulse0 
  mobile-broadband-provider-info mono-2.0-gac mono-gac mono-runtime 
  network-manager-gnome pulseaudio pulseaudio-esound-compat 
  pulseaudio-module-bluetooth{a} pulseaudio-module-gconf 
  pulseaudio-module-x11 pulseaudio-utils tomboy ubuntu-minimal udev upstart 
  x11-common 
0 packages upgraded, 0 newly installed, 0 to remove and 35 not upgraded.


Thanks :)

---

### Post by taavikko on 2009-08-11
Soapytheclown, just do it (nike tm)
they're held back because of new dependencies and dropped dependencies.
If uncertain, paste the "removed" portion here and we'll tell you...

---

