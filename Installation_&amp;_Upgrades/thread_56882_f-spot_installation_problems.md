---
title: "f-spot installation problems"
date: 2005-08-14
forum: Installation &amp; Upgrades
---

### Post by element on 2005-08-14
**Tried installing f-spot using synaptic and I get this...**

** (/usr/lib/f-spot/f-spot.exe:7499): WARNING **: The following assembly referenc ed from /usr/lib/f-spot/f-spot.exe could not be loaded:
     Assembly:   gnome-sharp    (assemblyref_index=7)
     Version:    1.0.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MON O_PATH environment variable, or in the location of the executing assembly (/usr/l ib/f-spot).


** (/usr/lib/f-spot/f-spot.exe:7499): WARNING **: The class Gnome.Program could n ot be loaded, used in /usr/lib/f-spot/f-spot.exe (token 0x0100012e)

Unhandled Exception: System.NullReferenceException: Object reference not set to a n instance of an object


[B]Then I tried installing it via the package from [http://www.gnome.org/projects/f-spot/](http://www.gnome.org/projects/f-spot/) 

when I run ./configure I get this...[/B]

checking for libgnome-2.0 >= 2.2 libgnomeui-2.0 >= 2.2 libexif >= 0.5.7 libexif < 0.7.0 gtkhtml-sharp >= 1.0 gconf-sharp >= 1.0 glade-sharp >= 1.0 gtk+-2.0 >= 2.4... Package gtkhtml-sharp was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtkhtml-sharp.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtkhtml-sharp' found

configure: error: Library requirements (libgnome-2.0 >= 2.2 libgnomeui-2.0 >= 2.2 libexif >= 0.5.7 libexif < 0.7.0 gtkhtml-sharp >= 1.0 gconf-sharp >= 1.0 glade-sharp >= 1.0 gtk+-2.0 >= 2.4) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.


[B]Can anyone help me so I can get f-spot running on ubuntu?  Has anyone had sucess with this app?

Thanks.[/B]

---

### Post by element on 2005-08-14
The answer was on this thread...

[http://ubuntuforums.org/showthread.php?t=48300&highlight=f-spot](http://ubuntuforums.org/showthread.php?t=48300&highlight=f-spot)

I installed Beagle and f-spot works now.

---

