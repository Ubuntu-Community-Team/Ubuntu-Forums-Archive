---
title: "Gnome Art Next Gen Won't Install in Karmic"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by booksnmore4you on 2009-11-19
[Gnome Art Next Gen]("http://developer.berlios.de/projects/gnomeartng/") looks sweet.  Unfortunately, there are no packages for Karmic and the earlier ones do not work in it.  

Has anyone had success compiling G A N G from source?  If so, what did you do?  Here are the errors I get:

```

books@books-desktop:~/gnomeartng-0.7.0$ ./compile
Package glade-sharp-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glade-sharp-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glade-sharp-2.0' found
Package gnome-sharp-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gnome-sharp-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gnome-sharp-2.0' found
Package gconf-sharp-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gconf-sharp-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gconf-sharp-2.0' found
error CS0006: cannot find metadata file `System.Windows.Forms.dll'
Compilation failed: 1 error(s), 0 warnings
books@books-desktop:~/gnomeartng-0.7.0$ 


```

---

### Post by cariboo on 2009-11-19
have you got libgconf2.0-cil installed?

---

### Post by booksnmore4you on 2009-11-19
Yes.  Same output.

In the gnomeartng-0.7.0 folder's READ ME it says 

> Running GNOME-Art Next Gen (GANG):
---------------------------
Please execute "sh runGnomeArtNG.sh" or "mono GnomeArtNg.exe" to run this project
When I do this without first compiling I get:

```
Cannot open assembly './GnomeArtNg.exe': No such file or directory.

```Stumped, here. #-o

---

### Post by 1981Neo on 2009-11-20
Hi there!

[B]Please note:
At this moment there is NO version of GANG for Karmic Koala! [/B]

I've compiled one at my office, but there are major changes concerning the GDM and splash so all that works at the moment (tested) are changing background images and icons.

I'll update the version as there is some spare time, but first I'll have to make some money to pay my bills... there was no single financial contribution for gnome-art-ng since one year...I have to assign priorities to ensure further development.

Greetings Tom

---

