---
title: "xscreensaver daemon doesn't seem to be running/xscreensaver daemon did not start"
date: 2009-02-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hanover.fiste on 2009-02-19
Sorry for the long title, but I'm having a problem that started after the upgrade to jaunty. I'm running gnome as the desktop. All updates have been applied, and I've tried restarting X as well as restarting the entire system.

Xscreensaver Setup always reports that the xscreensaver daemon doesn't seem to be running on the display and asks if I want to start it. Clicking OK results in the error that the xscreensaver daemon failed to start properly and that I should check my environment and path. ps -efww|grep screen shows the daemon running, and xscreensaver-demo runs OK except for the above named errors. Any ideas on exactly what I need to check? Everything else on the system is fine as far as I can tell.

The one question I had is whether or not xscreensaver should be writing a pid file or not?

---

### Post by [superman] on 2009-04-16
Hi 

I got the same error and I fixed it on xfce. I hope it's the same pb: I removed gnome-screensaver and installed xscreensaver but it wasn't launch automatically at start .

The pb was in my xinitrc file (/etc/xdg/xfce/xinitrc). There are several xinitrc files, I found out which one I need to modify in my $HOME in the log file .xsession-errors.

In this files I got 
```

# Launch xscreensaver (if available), but only as non-root user
if test $UID -gt 0 -a -z "$VNCSESSION"; then
 gnome-screensaver &
 if [ ! $? -eq 0]; then
  xscreensaver -no-splash &
 fi
fi

```
The pb was, depite gnome-screensaver was uninstalled, try to run it returned 0. So I commented the test and the call of gnome-screensaver and it works. 

Beside I have just check in an other computer with xscreensaver which worked at the installation, xinitrc file is different I have :
```

# Launch xscreensaver (if available), but only as non-root user
if test $UID -gt 0 -a -z "$VNCSESSION"; then 
    if test x"`which xscreensaver 2>/dev/null`" != x""; then
        xscreensaver -no-splash &
    elif test x"`which gnome-screensaver 2>/dev/null`" != x""; then
        gnome-screensaver &
    fi
fi 

```


I hope this can help you 

S.

---

