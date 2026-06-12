---
title: "Installed 8.04, File Open/Save Crashing!"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by mobius777 on 2008-06-05
I've just installed 8.04 on my HP 6000dv, and all is well except one major thing. 

*Every* time, in any application, when I try to Open (open file dialog) or Save (save a working file) the application just crashes. This is for all apps, OpenOffice, gedit, photo viewers, or anything. So it must be something with the Gnome open/save dialog box. 

The logs only show a Segfault occurred with no other useful information.

Please help!

---

### Post by mobius777 on 2008-06-05
One more thing... I just noticed that I *can* open files and save files if I'm root. Maybe that will help in diagnosing. So could it be a permissions issue?

Example: I open gedit from the menu (as a normal user). Clicking "open" causes gedit to instantly crash (segfault in log). However, opeing gedit from the command line as root, I can open and save all I want. I assume the same issue would be true for all other apps.

---

### Post by mobius777 on 2008-06-05
Well, I figured it out. It was nothing that I expected... but by trail and error I noticed that from my file browser (nautilus) bookmarks I could not access my Documents folder any more. But the documents folder was still there. I had earlier remapped it (in 7.10) to a different location.

Turns out, 7.10 is fine if you map to a path in this form: /path/path/etc/

However, in 8.04, it blows up! Once I remapped the book mark locations to start with file:/// (file:///path/path/etc/) my problems were solved.

So, in short, after upgrading to 8.10, make sure you check your nautilus bookmark if you've changed their locations in 7.10.

---

### Post by kevev on 2008-06-16
I can verify this. I had a wacky bookmark. It was something like %%ff%%ff%%ff% and so on. Just deleted it and everything is fine. :)

---

### Post by manca on 2008-07-27
This doesn't work for me. I don't have anything looking suspicios.

The problem occurs with both root ran programs and classic user ran programs. So gedit, firefox, and so on crash when save as or open dialogs are opened. However, shutting down gnome-settings-daemon make them work!

What could be the problem?

---

### Post by DavidEGrayson on 2008-07-27
Thank you for the great tip Mobius777!

I was having this exact same bug, and your solution worked for me.

For those who are extra noobish, like me, I'll explain it more clearly here:

[LIST=1]
[*] Open Nautilus.  There are many ways to do this, for example by typing `nautilus` or going to "Places" -> "Home Folder"
[*] In the "Bookmarks" menu of Nautilus, click "Edit Bookmarks"
[*] Make sure that each Bookmark Location starts with "file://"
[/LIST]

Now you can enjoy file Open/Save Dialogs in all your applications!

--David Grayson
[http://www.DavidEGrayson.com/](http://www.DavidEGrayson.com/)

---

### Post by trappy on 2008-08-03
I got the same problem; running openbox-session and the problem clearly have to do with gnome-settings-daemon - when I kill it, the save dialogs works just fine, though the my fonts suddenly is very big. 

When gnome-settings-daemon is running, every GTK-based app that I try to save / open from crashes with seg fault. Any ideas?

---

### Post by kill_bill on 2009-10-07
I had the same problem, fixing all the file:// didn't work, but removing all bookmarks helped - but that's not a nice solution

---

