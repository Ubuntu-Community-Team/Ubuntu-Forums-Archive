---
title: "intltool"
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by sirlost on 2010-08-02
so, I'm trying to compile banshee but when i run ./configure i get this message:

checking for intltool >= 0.35.0... ./configure: line 4377: intltool-update: command not found
 found
configure: error: Your intltool is too old.  You need intltool 0.35.0 or later.

so i open up the package manager to check intltool and it's version 0.35.0. i don't know if i'm a bit dim and missing something obvious or if my computer is just angry with me or what.

if anybody has any ideas or insight it would really be appreciated

---

### Post by labinnsw on 2010-10-31
> **sirlost said:**
> so, I'm trying to compile banshee but when i run ./configure i get this message:

checking for intltool >= 0.35.0... ./configure: line 4377: intltool-update: command not found
 found
configure: error: Your intltool is too old.  You need intltool 0.35.0 or later.

so i open up the package manager to check intltool and it's version 0.35.0. i don't know if i'm a bit dim and missing something obvious or if my computer is just angry with me or what.

if anybody has any ideas or insight it would really be appreciated

I am having the same problem. Care to say how it was solved?

[Never mind]("http://ubuntuforums.org/showpost.php?p=8334230&postcount=3")

---

### Post by jpka on 2010-12-27
same problem while configuring [pcb]("http://pcb.gpleda.org/")

```
checking for intltool >= 0.35.0... ./configure: line 14379: intltool-update: command not found
 found
configure: error: Your intltool is too old.  You need intltool 0.35.0 or later.

```

---

### Post by labinnsw on 2010-12-27
> **jpka said:**
> same problem while configuring [pcb]("http://pcb.gpleda.org/")

```
checking for intltool >= 0.35.0... ./configure: line 14379: intltool-update: command not found
 found
configure: error: Your intltool is too old.  You need intltool 0.35.0 or later.

```

The link to the solution is in my post.
> **aya2611 said:**
> [COLOR=Purple]I am new to Ubuntu and Ekiga and i have run into several problems as well during the compiling. 

About the problem u have mentioned , i have managed to solve it, so i think to save some time for you and for other people whom might run the same problem as i do. 
i will just post all the problems and solutions.  [/COLOR]

Hope this post helps ~ :D

When compiling Ekiga : 

  	 	 	 	 	 	  [COLOR=#000000][FONT=Times New Roman, serif][SIZE=2]**Error Message : **Checking for PTLIB... configure: error: Package requirements (ptlib >= 2.0.0) were not met:    No package 'ptlib' found 

**Solution:**[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Times New Roman, serif][SIZE=2](export package path where u save your stuff) - 
[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=2]$ export PKG_CONFIG_PATH=[/SIZE][/FONT]”[FONT=Times New Roman, serif][SIZE=2]home/lib/pkgconfig”[/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=2][/SIZE][/FONT][/COLOR]

 [SIZE=2][COLOR=#000000][FONT=Times New Roman, serif]**Error Message: **[/FONT][/COLOR]configure: error: Your intltool is too old. You need intltool 0.35.0 or later.[/SIZE]
 

 [SIZE=2][COLOR=#000000][FONT=Times New Roman, serif]**Solution:$ **[/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman, serif]sudo apt-get install intltool[/FONT][/COLOR][/SIZE]
 

 [SIZE=2][COLOR=#000000][FONT=Times New Roman, serif]**Error Message: **[/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman, serif]checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.10.0) were not met:  [/FONT][/COLOR]No package 'gtk+-2.0' found[/SIZE]
 

 [SIZE=2]**Solution **: $  sudo  apt-get install libgtk2.0-dev 
[/SIZE]

[SIZE=2][/SIZE]
[B][COLOR=Orange]If you are lazy and dont care about the memory space it might take. 
Just try to install everything to cut down your "search n fix error" time. [/COLOR]
[/B][SIZE=1]
[/SIZE]
[SIZE=1]**This is my 2nd last command:  **
[/SIZE]
 [SIZE=2]$sudo apt-get build-dep cheese[/SIZE]

[B]My last command (just copy and paste everything):

$ sudo aptitude install gnome-common libsasl2-dev gettext libgnome2-dev libldap2-dev libgconf2-dev autoconf libgnomeui-dev libxv-dev intltool  automake1.8 scrollkeeper libxml-parser-perl evolution-data-server-dev libavahi-common-dev libavahi-client-dev libavahi-glib-dev gnome-doc-utils libsigc++-2.0-dev libdbus-glib-1-dev libebook1.2-dev

[COLOR=Orange]Other problems u might encounter (no package found): 
[COLOR=Black]Go to System -> Administration -> Synaptic Package Manager 
then search and find the name to see if anything can be installed. 
[/COLOR][/COLOR][/B][SIZE=2][/SIZE] 
 


_***[COLOR=Red]After typing all these you should be able to make and make install. [/COLOR]***_:popcorn:
U can call me dummy , but it is truth i only start using Ubuntu for days =X

---

### Post by jpka on 2010-12-28
Thank you, it works)

---

### Post by RastaCalavera on 2011-01-18
Hey guys,

After following all of your commands I got this error:

1) were not met:

No package 'mono' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MONO_MODULE_CFLAGS
and MONO_MODULE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


I am trying to get banshee as well. What am I doing wrong? Thanks!!

---

### Post by RastaCalavera on 2011-01-18
Hey guys,

After following all of your commands I got this error:

1) were not met:

No package 'mono' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MONO_MODULE_CFLAGS
and MONO_MODULE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


I am trying to get banshee as well. What am I doing wrong? Thanks!!

---

### Post by bluepak on 2011-05-12
I am getting error below while trying to install cheese-3.01:

"checking for CHEESE... no
configure: error: Package requirements (  glib-2.0 >= 2.28.0   gobject-2.0 >= 2.28.0   gdk-pixbuf-2.0   gstreamer-0.10 >= 0.10.32   gstreamer-plugins-base-0.10 >= 0.10.32   cairo >= 1.10.0   pangocairo >= 1.28.0   clutter-1.0 >= 1.6.1   clutter-gst-1.0 >= 1.0.0   mx-1.0   gudev-1.0
  ) were not met:

No package 'clutter-1.0' found
No package 'clutter-gst-1.0' found
No package 'mx-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables CHEESE_CFLAGS
and CHEESE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
:confused:"

---

