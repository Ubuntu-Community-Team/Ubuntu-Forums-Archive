---
title: "AWN and nVidia drivers"
date: 2008-09-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by phenest on 2008-09-14
I'm posting here first because I don't know what is causing this. Therefore, I don't know who to report it to.

This is the ppa of AWN, but I get the same thing with the Synaptics version. Never had this problem in Hardy.

I have an nVidia GeForce 7950GTX. If I use the open source drivers, it's ok. If I use nVidia's drivers, I get the problem you see in the attachment. Also, if I use the open source drivers, the clock applet flashes (every second) over full-screen apps. If I use nVidia's drivers, there is no flashing.

---

### Post by phenest on 2008-09-17
The clock applet flashing issue is another bug: [bug 218322]("https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/218322")

---

### Post by ulukapata on 2008-09-17
try thiss...


[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by phenest on 2008-09-17
Is that relevant? Besides, Flash don't work for me 'cos it causes FF to crash, so it's currently disabled.

---

### Post by phenest on 2008-09-22
There appears to be posts deleted from this thread.:confused:

Anyway, this problem is happening regardless of what I use:

metacity or compiz
awn ppa or awn from synaptics

Somebody mentioned something about Python in another thread. I dunno.

Bug reported on Launchpad: [273326]("https://bugs.launchpad.net/awn/+bug/273326")

---

### Post by ronacc on 2008-09-22
I'm getting some of those effects but not all, I did discover a couple of things playing around with it , the thin verticle bars appear when I "activate " an app that does NOT activate , attempting to activate a second time causes a second vertical bar to appear , deactivating does not remove the bars . also deleteing ALL traces of awn from my /home does not remove either the running apps or the bars , where in heck are the config files that awn is actualy using the ones that were in /home weren't them ?

---

### Post by nanog on 2008-09-22
Which awn ppa are you using -- reacocard's or testing? I am using testing

```

deb http://ppa.launchpad.net/awn-testing/ubuntu intrepid main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu intrepid main

```

and do not have these problems (177 and 8400GS).

---

### Post by Efros on 2008-09-22
I get AWN to work but, no applets and the manager crashes as soon as I start it.

---

### Post by ronacc on 2008-09-22
tried the ppa that nanog recomended , it seems to have cleared thing up for me

---

### Post by phenest on 2008-09-23
> **nanog said:**
> Which awn ppa are you using -- reacocard's or testing? I am using testing

```

deb http://ppa.launchpad.net/awn-testing/ubuntu intrepid main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu intrepid main

```

and do not have these problems (177 and 8400GS).

Yep, same one. I have a 7950GTX. If I boot boot back into Hardy, AWN is fine. Hardy and Intrepid use the same /home partition, so it can't be any config file in there. And Hardy is also using the ppa.

---

### Post by Efros on 2008-09-26
Yep using nanogs recommended and Nvidia Beta works, although there is a white vertical line artifact on the deskbar when I use certain applets. Considering this is Alpha 6 its pretty good.

---

### Post by phenest on 2008-09-27
> **Efros said:**
> ...although there is a white vertical line artifact on the deskbar when I use certain applets.

Then it sounds like you have the same issue as me. Could you please help by adding anything you can to the bug report (post #4), please.

---

### Post by plun on 2008-09-27
> **phenest said:**
> Then it sounds like you have the same issue as me. Could you please help by adding anything you can to the bug report (post #4), please.

Well a vertical line means that a applet is broken.

As I understand it the AWN project has a "never ending discussion"
about a new version.  Maybe a Gentoo problem ?

EDIT

Start AWN from a terminal

> plun@plun:~$ avant-window-navigator

or with gdb

---

### Post by phenest on 2008-09-27
> **plun said:**
> Well a vertical line means that a applet is broken.

That is true, but this bug means you get a lot of these vertical lines. Some are wide vertical lines, some are narrow. Nothing to do with applets being broken in this case.

---

### Post by plun on 2008-09-27
> **phenest said:**
> That is true, but this bug means you get a lot of these vertical lines. Some are wide vertical lines, some are narrow. Nothing to do with applets being broken in this case.

Ok... check this


```
killall awn


avant-window-navigator
```


I have a few errors but it works.


```
plun@plun:~$ avant-window-navigator

(awn-applets-migration.py:7671): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `AwnConfigClient'
Screen is composited.
LOADED : /usr/share/applications/firefox.desktop
LOADED : /usr/share/applications/gnome-terminal.desktop
APPLET : /usr/share/avant-window-navigator/applets/taskman.desktop
APPLET : /usr/share/avant-window-navigator/applets/weather.desktop
APPLET : /usr/share/avant-window-navigator/applets/awnnotificationdaemon.desktop
APPLET : /usr/share/avant-window-navigator/applets/plugger.desktop
The following is an informational message only: 
notification-daemon: no process killed
First attempt failed:  The following is an informational message only: 
notification-daemon: no process killed
/usr/share/avant-window-navigator/applets/stacks/stacks_applet.py:410: Warning: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
  gtk.main()

GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
aborting...

(awn-applet-activation:7618): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
/usr/lib/python2.5/site-packages/awn/extras/AWNLib.py:1518: Warning: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
  gtk.main()

```


Also check this page about dependencies

[http://wiki.awn-project.org/Awn_Extras:Dependency_Matrix](http://wiki.awn-project.org/Awn_Extras:Dependency_Matrix)

.
.

---

### Post by plun on 2008-09-28
I took the time and tested....

I noticed that "Awn Notification Daemon" seems to be buggy.

Also that a "white box" occurs (also the white line) when some applets is placed on the right.

If I then for example have the Cairo clock on the right this "white box" is gone.

(You can move applets with drag & drop from the manager)

Going to test a little bit more.

---

### Post by Efros on 2008-09-28
> **phenest said:**
> Then it sounds like you have the same issue as me. Could you please help by adding anything you can to the bug report (post #4), please.

I'll have a look at it when I get back to the machine on monday.

---

### Post by phenest on 2008-09-28
This is definitely a 'drawing' problem somewhere along the line. If you check the bug I reported, you will see I've posted another screenshot where the PyNot applet has an artifact from the Weather applet.

This is something that has only become apparent in Intrepid.

---

### Post by wizard10000 on 2008-10-13
> **phenest said:**
> I'm posting here first because I don't know what is causing this. Therefore, I don't know who to report it to.

Obligatory "me too" post.

I've seen this with Intrepid and awn from both Ubuntu repos and from awn trunk.  Interestingly, this didn't happen with awn trunk under Hardy.

Can't address the flashing clock thing as I don't use it but I get artifacts on awn's dock.

---

### Post by phenest on 2008-10-15
> **wizard10000 said:**
> Can't address the flashing clock thing as I don't use it but I get artifacts on awn's dock.

The clock issue turned out to be the nv driver and unrelated to this bug.

---

