---
title: "Remove pulseaudio without removing ubuntu desktop"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by miwaypet on 2009-10-11
Is there a way to remove pulseaudio without removing the ubuntu desktop. Myaudio is stuttering badly and i want/need to dump pulse audio. Can't play podcasts, open arena, or movies without that crap sound. Thanx in advance.

---

### Post by coldReactive on 2009-10-11
ubuntu-desktop as far as I know is a metapackage. It doesn't actually remove anything.

---

### Post by VMC on 2009-10-11
> **miwaypet said:**
> Is there a way to remove pulseaudio without removing the ubuntu desktop. Myaudio is stuttering badly and i want/need to dump pulse audio. Can't play podcasts, open arena, or movies without that crap sound. Thanx in advance.

There's a recent pulseaudio update: Version: 1:0.9.19-0ubuntu1

---

### Post by lithorus on 2009-10-12
> **miwaypet said:**
> Is there a way to remove pulseaudio without removing the ubuntu desktop. Myaudio is stuttering badly and i want/need to dump pulse audio. Can't play podcasts, open arena, or movies without that crap sound. Thanx in advance.
The main point of Karmic right now is to beta-test it, not to have a production system. If you want to help this process, file a bug report explaining your problem in details, so the problem can be fixed. I'm sorry to say that getting rid of pulseaudio is not a fix.

---

### Post by cyberkilla on 2009-10-12
> **glaze said:**
> The first answer in this thread answers your question.

It's not exactly the definitive answer.

What will happen if the metapackage is removed? Presumably, if another update rolls in, it will reinstall ubuntu-desktop, and all of the junk it depends on?

Seems a bit restrictive and forceful. Please tell me it doesn't work that way:P

---

### Post by coldReactive on 2009-10-12
> **cyberkilla said:**
> It's not exactly the definitive answer.

What will happen if the metapackage is removed? Presumably, if another update rolls in, it will reinstall ubuntu-desktop, and all of the junk it depends on?

Seems a bit restrictive and forceful. Please tell me it doesn't work that way:P

If an update installs ubuntu-desktop, everything that comes with ubuntu-desktop is installed as well. No questions asked, no way to get around it. There's a very slim chance of that happening though.

---

### Post by seeker5528 on 2009-10-12
> **miwaypet said:**
> Is there a way to remove pulseaudio without removing the ubuntu desktop.

If you use Synaptic.....

Go to 'Settings --> preferences'

On the 'General' tab uncheck the 'Consider recommended packages as dependencies' box.

Click 'OK'

Make sure 'Status' and 'ALL' sre selected in the left column.

Single click any package in the main window to put the focus there.

Type 'pulse' to bring you to the pulse* section of the package listing.

You should be able to right click and choose 'Mark for complete removal' on pulseaudio and any of the pulseaudio-* packages without having the remove the gnome-desktop metapackage.

This leaves a few pulse audio library packages, but they are depended on by other packages and are not active parts of Pulse Audio so are OK.

Once you are done you can go back to the settings menu and check the 'Consider recommended packages as dependencies' box. 

Any time something wants to pull in or update a pulse audio related package I cancel the install, updating everything but those packages, then uncheck the 'Consider recommended packages as dependencies' box so only the minimum required pulseaudio packages get installed, then check the box again when I am done.

Related side note: 

Looks like the dependents fucntion of Synaptic is screwed up. It shows gnome-media and some other other packages as dependents of pulseaudio, when those other packages have pulseaudio listed as a recommended package, no matter which way you have the 'recommended packages' option set in the options.

And no I don't feel any obligation to test pulseaudio, there are plenty of people testing it who actually want to have it installed. :P

Later, Seeker

---

