---
title: "Deluge  fails to start after running 24 hours"
date: 2009-04-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by zenithdave on 2009-04-02
Hello, deluge has been running fine for 24 hours on eee laptop(fresh jaunty install)

The wireless stopped working but a router and  computer reboot cured that.

Deluge opens its window but nothing appears in it and just 1 time i had a error message about libc6 being out of date. 

I ran in a terminal.....

```
***********-laptop:~$ deluge
1.1.5
/var/lib/python-support/python2.6/deluge/ui/gtkui/mainwindow.py:51: GtkWarning: gtk_toolbar_set_icon_size: assertion `icon_size != GTK_ICON_SIZE_INVALID' failed
  "glade/main_window.glade"))
Unhandled exception in thread started by 
Error in sys.excepthook:

Original exception was:
```

Anyone know if this is a jaunty or deluge problem !! most odd

Thanks

---

### Post by binbash on 2009-04-02
This may not be a deluge problem because my download server uses deluge latest and it is online for 35 days.You can restart it without any problems.It is fedora btw

---

### Post by zenithdave on 2009-04-02
It wont start at all now ,, same problem every time.

thanks

---

### Post by binbash on 2009-04-02
There is a bug report for this at launchpad, and according to this thread : 
[http://forum.deluge-torrent.org/viewtopic.php?f=7&t=16455&p=79105](http://forum.deluge-torrent.org/viewtopic.php?f=7&t=16455&p=79105)

it is broken

---

### Post by zenithdave on 2009-04-02
Thanks for finding that, i was not sure to try to report it as a bug or not.

---

