---
title: "no gdm, loads with sudo gdm"
date: 2009-07-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2009-07-15
Well, I done it.  Installed Kubuntu desktop and switched to kdm, had some fun over there but now I'm back....  except cannot get gdm to start itself. I know to set it in /etc/X11/default-display-manager set to gdm.  but when it loads it drops to tty1, sudo gdm and there it is.

I saw in the huuugggge gdm thread where it was mentioned but I couldn't figure out (or find) the fix.

any help?


Also as a side note, I'm using kdm but login in as gnome session.  compiz works everytime.  When using gdm and doing sudo gdm, cannot get compiz to work to save me.  Just thought I'd share.

---

### Post by wayne_cat on 2009-07-15
first thing to check ... maybe a typo:

```
root@macbook:~# cat /etc/X11/default-display-manager 
/usr/sbin/gdm
root@macbook:~# 

```and also interesting ... the gdm log files in:

```
/var/log/gdm
```still problems .. try to reinstall gdm with:

```
sudo apt-get remove --purge gdm
sudo apt-get install gdm
```

---

### Post by buzzmandt on 2009-07-15
```
buzzmandt@buzzmandt-laptop:~$ cat /etc/X11/default-display-manager 
/usr/bin/gdm
buzzmandt@buzzmandt-laptop:~$ 

```

no oopsies there



greeter.log is showing something saying "this should not happen".  Compare yours and see if you're getting this too.
```
(gnome-settings-daemon:2827): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:2827): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Window manager warning: Failed to read saved session file /var/lib/gdm/.config/metacity/sessions/101c17681991787a0e12476761483556300000028210006.ms: Failed to open file '/var/lib/gdm/.config/metacity/sessions/101c17681991787a0e12476761483556300000028210006.ms': No such file or directory
** (process:2833): DEBUG: Greeter session pid=2833 display=:0.0 xauthority=/var/run/gdm/auth-for-gdm-0r37Lp/database
gdm-simple-greeter[2833]: GLib-GObject-CRITICAL: g_param_spec_flags: assertion `G_TYPE_IS_FLAGS (flags_type)' failed
gdm-simple-greeter[2833]: GLib-GObject-CRITICAL: g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0xe00021 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0xe00021 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
gdm-simple-greeter[2833]: WARNING: Unable to lookup user name buzzmand: Success
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0xe00021 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!
```


and slave.log
```
gdm-session-worker[2835]: pam_unix(gdm:session): session opened for user buzzmandt by (uid=0)
gdm-session-worker[2835]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
```

the 0.log is huge so I've posted it here [http://pastebin.com/m1f460c5f](http://pastebin.com/m1f460c5f)
I don't see any thing critical in there, but you might see something I don't.  


```
sudo apt-get remove --purge gdm
sudo apt-get install gdm
```
Had done this before, but just for giggles I did it again at your suggestion.  Everything purges, then installs just fine.  reboot and have text login tty1 only.  login, sudo gdm, then everything runs quite nicely after that, like it should.


Just a side note, I've been working on this for a few days with google.  I just can't get it going

---

### Post by wayne_cat on 2009-07-15
no oopsies there ... really ... are you shure? :biggrin:


/usr/**[COLOR=Red]s[/COLOR]**bin/gdm

---

### Post by buzzmandt on 2009-07-15
Ahhh, &Y*(&(&(&(&^%$%^&*&^%$#ERFGBNMKUYTGFH*&^%

um, thanks.  lol.  

Why did it work with all the other dms?
I used kdm, wdm, xdm, and gdm.  edited that line for all 4 of them and it worked for all but gdm.

that's very interesting.

Thats my duuh huuhh moment of the week.

guess that shows why it's always best to get another opinion when you're stumped, probably overlooking something really simple.

---

### Post by buzzmandt on 2009-07-15
Ok, that worked of course,  thanks wayne_cat.  3 days I worked on that and .... man....

oh well

Everything is working on my sys now, wifi problem has a work around and a fix should be comming soon (ath5k).  gdm loads now, 

one issue left with the new kernel, that's my intel graphics are sluggish, but that's a post for another thread.  time to do some searching and see if anyone else has issues.

---

### Post by wayne_cat on 2009-07-15
gdm is the only display manger that "lives" in /usr/[COLOR=Red]s[/COLOR]bin. The others settle in /usr/bin

you can find their path with "which"


```
root@macbook:~# which gdm
/usr/sbin/gdm
root@macbook:~#
```

---

### Post by SushiR on 2009-07-15
> **wayne_cat said:**
> gdm is the only display manger that "lives" in /usr/[COLOR=Red]s[/COLOR]bin. The others settle in /usr/bin

Never noticed it. But it's a bit weird, isn't it?

---

### Post by wayne_cat on 2009-07-15
> **SushiR said:**
> Never noticed it. But it's a bit weird, isn't it?

nothing wrong with the path (for a Gnome user) ;)

[http://www.linfo.org/usr_sbin.html](http://www.linfo.org/usr_sbin.html)

---

