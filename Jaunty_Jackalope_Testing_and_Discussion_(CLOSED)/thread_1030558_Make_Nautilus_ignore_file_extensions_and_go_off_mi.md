---
title: "Make Nautilus ignore file extensions and go off mime-type instead?"
date: 2009-01-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jfernyhough on 2009-01-04
I'm tired of Nautilus saying it doesn't know how to open a .log or .nfo or whatever when it's gone and made an icon thumbnail. It knows damned well it's a text file but refuses to just open it in Gedit.

Is there a way of making it ignore the file extension (i.e. stop it working like Windows Explorer) and pay attention to the MIME-type? I mean, if the file has no file extension it does this /anyway/ ffs.

It also means that if I've misnamed a JPG (e.g. as PNG - try it) or ZIP (7z etc) it will open correctly, rather than, for example, File Roller coming up with a "cannot open archive" or whatever.

Just thinking about the misnamed image file. IrfanView in Windows detects the correct file type and offers to rename. Image Viewer should either do this or ignore it.

---

### Post by Gina on 2009-01-04
+1  I get particularly annoyed when I try to open .txt files and it refuses - knowing full well it's a text file to be opened with Gedit!

---

### Post by ronacc on 2009-01-04
I am constantly amazed when that don't happen, it was normal operation on the amiga 20+ years ago that it ignored extensions and paid attention to what the file really was .

---

### Post by damis648 on 2009-01-04
Yea, so what can we do about this? :popcorn:

---

### Post by gnomeuser on 2009-01-04
> **damis648 said:**
> Yea, so what can we do about this? :popcorn:

File a bug against Nautilus -> bugzilla.gnome.org

---

### Post by MaX on 2009-01-05
> **jfernyhough said:**
> I'm tired of Nautilus saying it doesn't know how to open a .log or .nfo or whatever when it's gone and made an icon thumbnail. It knows damned well it's a text file but refuses to just open it in Gedit.

Is there a way of making it ignore the file extension (i.e. stop it working like Windows Explorer) and pay attention to the MIME-type? I mean, if the file has no file extension it does this /anyway/ ffs.

It also means that if I've misnamed a JPG (e.g. as PNG - try it) or ZIP (7z etc) it will open correctly, rather than, for example, File Roller coming up with a "cannot open archive" or whatever.

Just thinking about the misnamed image file. IrfanView in Windows detects the correct file type and offers to rename. Image Viewer should either do this or ignore it.

Why don't you just right-click on it and choose Propertis and then in Open With specify which program to use for this file type.

BTW I tried renaming a text file to .nfo and .log (and others) and it still opened it with Gedit on double click so I don't understand your problem.

I could only reproduce your problem when I renamed it to .png and Ubuntu then tried to use Eye of Gnome which didn't work.

---

### Post by ronacc on 2009-01-05
because some prgs apearently write themselves into "open with" I sometimes get such bizzare things as xine trying to open pdf files or abiword opening .txt files instead of gedit .

---

### Post by MaX on 2009-01-05
> **ronacc said:**
> because some prgs apearently write themselves into "open with" I sometimes get such bizzare things as xine trying to open pdf files or abiword opening .txt files instead of gedit .

I'm talking about the open with in Properties, and when you've selected the one you want there, the default will not change unless you change it in some way (like uninstalling gedit)

---

