---
title: "GTK+ 2.0 Installed?"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by CrimsoniteX on 2008-03-25
From what I understand, Ubuntu 7.10 has all the development tools required for GTK+ 2.0 right? I thought I verified them all, however when trying to compile this tutorial program:
```
#include <gtk/gtk.h>

int main( int   argc,
          char *argv[] )
{
    GtkWidget *window;
    
    gtk_init (&argc, &argv);
    
    window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    gtk_widget_show  (window);
    
    gtk_main ();
    
    return 0;
} 
```

I get this error:
```
crimson@crimson-laptop:~/Documents/projects$ gcc main.c -o main
main.c:1:21: error: gtk/gtk.h: No such file or directory
main.c: In function ‘main’:
main.c:6: error: ‘GtkWidget’ undeclared (first use in this function)
main.c:6: error: (Each undeclared identifier is reported only once
main.c:6: error: for each function it appears in.)
main.c:6: error: ‘window’ undeclared (first use in this function)
main.c:10: error: ‘GTK_WINDOW_TOPLEVEL’ undeclared (first use in this function)

```

Does anyone have any ideas? Sorry i'm a newbie at Linux :confused:

---

### Post by scragar on 2008-03-25
```
gcc main.c -o main pkg-config --cflags --libs gtk+-2.0
```I think.

personaly I always run tests using binfmtc and the shebang:
```
/*BINFMTC: `pkg-config --cflags --libs gtk+-2.0`
*/
```so I could be wrong.

---

### Post by CrimsoniteX on 2008-03-25
I'm not sure what you mean, the output from the one you recommended is as follows:
```
crimson@crimson-laptop:~/Documents/projects$ pkg-config --cflags --libs gtk+-2.0
-I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12  -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXcomposite -lXdamage -lpango-1.0 -lcairo -lX11 -lXfixes -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
```

I am just curious why it is not compiling, and how I can fix it, thanks!

---

### Post by scragar on 2008-03-25
you miss understood, I think you need to change your compiling line to something like:
```
gcc main.c -o main pkg-config --cflags --libs gtk+-2.0
```
although again, I cannot be 100% certain since I tend to let binfmtc handle the compiling.

---

### Post by CrimsoniteX on 2008-03-25
Ohhhh, my fault the output of that is:
```
crimson@crimson-laptop:~/Documents/projects$ gcc main.c -o main pkg-config --cflags --libs gtk+-2.0
gcc: pkg-config: No such file or directory
gcc: gtk+-2.0: No such file or directory
cc1: error: unrecognized command line option "-fcflags"
cc1: error: unrecognized command line option "-flibs"
```

:confused:

---

### Post by dizee on 2008-03-25
Not sure if this'll fix the problem but the tools for compiling GTK2.0 were not installed by default on my machine. Check if the package "libgtk2.0-dev" is installed.

---

### Post by scragar on 2008-03-25
oops, put the single quotes around it, and it sort of compiled my test program

```
gcc main.c -o main 'pkg-config --cflags --libs gtk+-2.0'
```

---

### Post by CrimsoniteX on 2008-03-25
> **dizee said:**
> Not sure if this'll fix the problem but the tools for compiling GTK2.0 were not installed by default on my machine. Check if the package "libgtk2.0-dev" is installed.

Yes. I just reinstalled it to be sure, same thing though...

@scragar
I put single quotes around it, but same output as with: 
gcc main.c -o main

---

### Post by CrimsoniteX on 2008-03-25
WOW I am an idiot, I need to stop copy/pasting incorrectly :mad:
The correct command was:
```
gcc base.c -o base `pkg-config --cflags --libs gtk+-2.0`
```

Thanks for the input guys!

---

