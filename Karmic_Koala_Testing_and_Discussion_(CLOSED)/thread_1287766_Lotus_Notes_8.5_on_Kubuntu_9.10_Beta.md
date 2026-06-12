---
title: "Lotus Notes 8.5 on Kubuntu 9.10 Beta"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Lem on 2009-10-10
I have installed Lotus Notes on Kubuntu Beta, and despite it opening fine, connecting and telling me I have new mail, it doesn't actually display anything in the main window (see screenshot).
Any ideas out there? I had no problems under Ubuntu 9.04. I have installed libgnomeui which is apparently required for KDE4.

---

### Post by rrottier on 2009-10-12
I am having the same issue.

---

### Post by vitas on 2009-10-12
The same problem. Lotus Notes 8.5 beta 2, but Ubuntu 9.10, I even reinstalled Lotus Notes. In 9.4 was everything OK.

---

### Post by ploum on 2009-10-12
same problem here. Lot of java tracebacks in the console

---

### Post by ploum on 2009-10-12
The bug about that :
[https://bugs.edge.launchpad.net/ubuntu/+source/gtk+2.0/+bug/398250](https://bugs.edge.launchpad.net/ubuntu/+source/gtk+2.0/+bug/398250)

---

### Post by ploum on 2009-10-12
It looks like there are two possible workarounds :

1) patching libgtk with the patch provided here :
[http://bugzilla.gnome.org/show_bug.cgi?id=590404](http://bugzilla.gnome.org/show_bug.cgi?id=590404)

Problem : requires recompiling and repackaging at each update of the libgtk package.


2) putting libgdk_pixbuf-2.0.so.0.1702.0 libgdk_pixbuf_xlib-2.0.so.0.1702.0 libgdk-x11-2.0.so.0.1702.0 libgtk-x11-2.0.so.0.1702.0 in the notes directory.

Problem : finding those files as there were part of an old version of the libgtk package.

---

### Post by ploum on 2009-10-12
I've tried solution 2) but with a 1800. version of the files.

It worked fine once then, on restart, the bug reappeared. Weird…

---

### Post by rrottier on 2009-10-16
Solution 2 works for me.  There is a link to the files in [https://bugs.edge.launchpad.net/ubuntu/+source/gtk+2.0/+bug/398250](https://bugs.edge.launchpad.net/ubuntu/+source/gtk+2.0/+bug/398250).

---

### Post by klockej on 2009-10-19
I am glad I am not the only person having this issue. I figured it was a Java issue and have been chasing that.I will give this a shot after lunch and hopefully it corrects the problem.

---

### Post by klockej on 2009-10-19
Solution 2 also worked for me. I downloaded those files and placed them in the notes folder and everything started working fine.

---

