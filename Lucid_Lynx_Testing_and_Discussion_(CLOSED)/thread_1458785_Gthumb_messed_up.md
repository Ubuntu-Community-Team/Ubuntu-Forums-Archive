---
title: "Gthumb messed up"
date: 2010-04-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by forcecore on 2010-04-20
Looks like someone has decreased Gthumb version back to stoneage version so i used nilarimogard repo for 2.11.3 version but it wont run and terminal shows some clutter error, where i can get better clutter thing to destroy Ubuntu version. Please devs uptate to 2.11.3 because this is much better.

---

### Post by ranch hand on 2010-04-20
Looks fine to me.

---

### Post by forcecore on 2010-04-20
what version?

---

### Post by ranch hand on 2010-04-20
2.10.11

---

### Post by forcecore on 2010-04-20
i use 2.11.3 from [https://launchpad.net/~nilarimogard/+archive/webupd8](https://launchpad.net/~nilarimogard/+archive/webupd8) because developers dumped new version.

Is there someone else who uses 2.11.3

---

### Post by forcecore on 2010-04-20
i found problem and i tested that older 1.0.8 clutter works and newer 1.2.4 fails and terminal message is:

** ERROR **: Unable to initialize GtkClutter
aborting...
Trace/breakpoint trap (core dumped)

i wait RC, maybe it just temporary error.

---

### Post by Killigrew on 2010-04-20
> **forcecore said:**
> i use 2.11.3 from [https://launchpad.net/~nilarimogard/+archive/webupd8]("https://launchpad.net/%7Enilarimogard/+archive/webupd8") because developers dumped new version.

Is there someone else who uses 2.11.3

I use the same version from the ppa.
The original lucid version got reverted to an older one
because of to many bugs in the new one.
The funny thing is that the "new" old version gave me segmentation fault errors
when i opened pictures from a certain folder.

2.11.3 is working like a charm and the basic picture editing capabilitys are quite nice :)

greetings

---

### Post by mjc1 on 2010-04-21
There was a commit to gthumb git master a few days ago called "Allow to run the application if clutter initialization fails".

This might be what is causing clutter problems. This fix will appear in 2.11.4.

You can compile and install the git version, of course. See [http://live.gnome.org/gthumb/development](http://live.gnome.org/gthumb/development)

- Mike

---

### Post by StuartN on 2010-04-21
> **ranch hand said:**
> 2.10.11

It was reverted back to version 2.10.11-0 used in Jaunty, rather than 2.10.11-1 used in Karmic.

---

### Post by forcecore on 2010-04-22
Looks like i found cause of that error: [http://ubuntuforums.org/showthread.php?t=1459417](http://ubuntuforums.org/showthread.php?t=1459417)

END OF THREAD

---

