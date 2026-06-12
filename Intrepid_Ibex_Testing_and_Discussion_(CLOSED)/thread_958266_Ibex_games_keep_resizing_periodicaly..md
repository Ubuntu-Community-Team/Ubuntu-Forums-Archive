---
title: "Ibex games keep resizing periodicaly."
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mike310z on 2008-10-25
I have the latest ibex an ATI 9800 and compiz. I can finally run Linux on this machine because Ibex brings my wireless card to life.

My problem is that full screen games such as Glest, ET Quake Wars and Nexuiz, resize to a window every few minuets without me touching anything.

This really makes it hard to avoid being fragged, especially in ET Quake Wars because once resized, all keyboard and mouse control is lost and a hard reboot is required.

I closed everything I could to help ensure no task I know about could be  causing this, does any one have any ideas ?

Thanks 
Mike

---

### Post by treesurf on 2008-10-25
I had this problem as well and discovered that the culprit was compiz.  I solved it by switching to metacity whenever running full screen games.

to switch to metacity in terminal type: metacity --replace
to switch back to compiz:  compiz --replace

---

### Post by mike310z on 2008-10-25
Thanks, that works :-)

The only down side is that whilst in metacity the window decorations are missing.
I posted a bug since this might be more wide spread than my machine
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/289171](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/289171)

---

### Post by fabertawe on 2008-10-25
This is a well known problem with Compiz, normally solved by unticking 'Undirect Fullscreen Windows' in the 'General' section of 'CompizConfig Settings Manager'.

---

### Post by mike310z on 2008-10-25
Thanks that mostly works, I installed 'CompizConfig Settings Manager' so that I could try it.
By un selecting Undirect Fullscreen Windows, the screen flickers to minimized and then comes back, which is still not quite a complete solution.

I am surprised there is not a bigger fuss over this, it appears to be fairly fundamental, but it sounds like its well known.

---

