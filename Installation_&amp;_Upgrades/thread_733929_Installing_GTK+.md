---
title: "Installing GTK+"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by henderbops on 2008-03-24
Hey, I've just installed GTK+ package on Ubuntu 7.10 (package name: libgtk2.0-0) using Synaptic Package Manager.. I am using a simple helloworld program to test if it works and its coming up with a lot of errors..

```

#include <gtk/gtk.h>

void
hello (GtkWidget *widget, gpointer data)
{
        g_print ("Hello World\n");
}

gboolean
delete_event(GtkWidget *widget, GdkEvent *event, gpointer data)
{
        g_print ("delete event occurred\n");
        return TRUE;
}

void
destroy (GtkWidget *widget, gpointer data)
{
        gtk_main_quit ();
}

int
main (int argc, char *argv[])
{
        GtkWidget *window;
        GtkWidget *button;

        gtk_init (&argc, &argv);

        window = gtk_window_new (GTK_WINDOW_TOPLEVEL);

        gtk_signal_connect (GTK_OBJECT (window), "delete_event",
                            GTK_SIGNAL_FUNC (delete_event), NULL);

        gtk_signal_connect (GTK_OBJECT (window), "destroy",
                            GTK_SIGNAL_FUNC (destroy), NULL);

        gtk_container_border_width (GTK_CONTAINER (window), 10);

        button = gtk_button_new_with_label ("Hello World");

        gtk_signal_connect (GTK_OBJECT (button), "clicked",
                            GTK_SIGNAL_FUNC (hello), NULL);

        gtk_signal_connect_object (GTK_OBJECT (button), "clicked",
                                   GTK_SIGNAL_FUNC (gtk_widget_destroy),
                                   GTK_OBJECT (window));

        gtk_container_add (GTK_CONTAINER (window), button);

        gtk_widget_show (button);

        gtk_widget_show (window);

        gtk_main ();

        return 0;
}

```

Originally the errors start with the gtk/gtk.h file not being found so after a little exploration I found that in "/usr/include" there is a folder named gtk-2.0 in which contains gtk/gtk.h so I tried changing #include<gtk/gtk.h> to #include<gtk-2.0/gtk/gtk.h.

This now means that the compiler can find gtk.h but now every file that gtk.h tries to include cannot be found by the compiler, which means I get an error message for every file that is to be included..

```

/usr/include/gtk-2.0/gtk/gtk.h:31:21: error: gdk/gdk.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:32:32: error: gtk/gtkaboutdialog.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:33:31: error: gtk/gtkaccelgroup.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:34:31: error: gtk/gtkaccellabel.h: No such file or directory
/usr/include/gtk-2.0/gtk/gtk.h:35:29: error: gtk/gtkaccelmap.h: No such file or directory
... etc etc.

```

I was wondering what I have done wrong when installing the GTK+ development package. I am guessing I have installed the wrong package, however the header files etc. appear to be all there.

Cheers,
Jonathon.

---

### Post by bashologist on 2008-03-24
Maybe try this?
[http://library.gnome.org/devel/gtk-tutorial/stable/c39.html](http://library.gnome.org/devel/gtk-tutorial/stable/c39.html)

Maybe try compiling something like this?
```
gcc base.c -o base `pkg-config --cflags --libs gtk+-2.0`
```

That's usually the problem. I don't know.

---

### Post by henderbops on 2008-03-30
Yeah compiling with "`pkg-config --cflags --libs gtk+-2.0`" fixes the problem. Is there a way to configure gcc so I don't have to do this every single time I want to compile a GTK application?

Cheers,
Jonathon.

---

