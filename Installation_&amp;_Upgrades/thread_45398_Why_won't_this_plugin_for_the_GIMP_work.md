---
title: "Why won't this plugin for the GIMP work?"
date: 2005-06-29
forum: Installation &amp; Upgrades
---

### Post by john_walsh54 on 2005-06-29
The only easy to use Red Eye Removal tool I could find for Gnome was the Red Eye plugin for the GIMP. Anyway I followed the [Red Eye plugin install instructions](http://registry.gimp.org/file/redeye.c?action=view&id=4215) but it didn't work. Below is the output. If you can tell me how to fix it I would be grateful.

john@ThinkPad:~$  gimptool-2.0 --install redeye.c
/usr/bin/install -c -d /home/john/.gimp-2.2/plug-ins
i386-linux-gcc -Wall -g -O2 -I/usr/include/gimp-2.0 -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -o /home/john/.gimp-2.2/plug-ins/redeye redeye.c -L/usr/lib -lgimpui-2.0 -lgimpwidgets-2.0 -lgimp-2.0 -lgimpcolor-2.0 -lgimpmath-2.0 -lgimpbase-2.0 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangoxft-1.0 -lpangox-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
/usr/bin/gimptool-2.0: line 327: exec: i386-linux-gcc: not found
john@ThinkPad:~$ sudo  gimptool-2.0 --install redeye.c
Password:
/usr/bin/install -c -d /home/john/.gimp-2.2/plug-ins
i386-linux-gcc -Wall -g -O2 -I/usr/include/gimp-2.0 -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -o /home/john/.gimp-2.2/plug-ins/redeye redeye.c -L/usr/lib -lgimpui-2.0 -lgimpwidgets-2.0 -lgimp-2.0 -lgimpcolor-2.0 -lgimpmath-2.0 -lgimpbase-2.0 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangoxft-1.0 -lpangox-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
/usr/bin/gimptool-2.0: line 327: exec: i386-linux-gcc: not found
john@ThinkPad:~$

Alternatively, you could suggest an application that has an easy to use Red Eye Removal Tool

John

---

### Post by tomchuk on 2005-06-30
Doesn't look like you don't have a compiler installed. apt-get install build-essential should do it

---

### Post by john_walsh54 on 2005-07-01
Tomchuk
Thank you.
I installed build-essentials using Synaptic and the Red Eye Removal plugin installed itself and works perfectly.
I still have a couple of questions, which I hope you could answer please:
For future reference, I would be grateful if you told me how you identified build-essentials needed to be installed?
I always thought Synaptic would get the components required to install (libgimp2.0-dev) package but it didn't install build-essentials in this case. Why?

Kind Regards

John

---

### Post by tomchuk on 2005-07-01
build-essential is the meta-package for the minimum set of tools you need to compile stuff. There's no real way to figure out on your own that the package exists and will solve your problem - barring knowing what you're looking for and some clever apt-cache searching. I've installed Debian and Ubuntu on a few machines over the years, and I guess probably learned about build-essential the same way you did; Except, I think I had someone on #debian tell me with all caps and a few profanities ;)

APT errs on the side of minimalism - for example if you install kernel sources, it doesn't install libncurses5-dev which is needed for menuconfig. I guess it's safer to assume that people edit their .config by hand than to install unneeded packages.

---

