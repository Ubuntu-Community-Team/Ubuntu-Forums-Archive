---
title: "Nautilus rocks hard now"
date: 2008-08-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Bou on 2008-08-05
Hi, you probably know that Nautilus recently got tab support. That's pretty awesome on its own, but there's another recent feature that's even cooler in my opinion, and that you might not know.

The pathbar buttons now behave like real buttons. You can drag any Nautilus item to and from them. So you can drag a file to the current folder's parent to move the file there, drag a pathbar button to the desktop to move the folder there, or even middle-drag a pathbar button to get the move / copy menu. You can also drag a pathbar button to a tab! Also, you can middle-click a pathbar button to open that folder in a new tab.

All in all, this makes Nautilus much more flexible and handy than it has ever been before :)

---

### Post by Gina on 2008-08-05
Sounds good :)  (Though I haven't got a middle mouse button)

---

### Post by plun on 2008-08-05
Yup, great features  :)


Another function which crashes for me is iso-mountings.

This was introduced within Hardy but a "hidden" function.

- Right click on a iso and "Open with" > "Archive mounter".

- The mounted iso appears as a shortcut.


But... it crashes directly for me if I tries to open it.

Bug ?   Can anyone confirm ?  :)

Picture
[[img]http://pix.nofrag.com/4/b/d/8a6749e5be45c0d72daf1ca82c018t.jpg[/img]](http://pix.nofrag.com/4/b/d/8a6749e5be45c0d72daf1ca82c018.html)

---

### Post by kahlil88 on 2008-08-05
I'm so happy Nautilus has tab support now! I used KDE for 2 years, and gradually realized that I completely **hated** it! In the end, the only thing holding me back was Konqueror, but I decided that I didn't even care. I've tried using [PCManFM]("http://pcmanfm.sourceforge.net/"), but aside from the tabs, it kinda bugs me (doesn't sort properly, no FTP support, doesn't show symlink sources). What a relief I can dump it soon! Why must September be so far away?!

---

### Post by deepclutch on 2008-08-05
nautilus with tabs ? I liked the old way though.

---

### Post by amano on 2008-08-05
Just don't middleclick something and it is the old way then? And you can even turn off the behaviour in gconf.

---

### Post by volanin on 2008-08-05
> **Gina said:**
> Sounds good :)  (Though I haven't got a middle mouse button)

You can middle-click by pressing both the left and right buttons
at the same time!
:)

---

### Post by ViRMiN on 2008-08-05
> **plun said:**
> Yup, great features  :)


Another function which crashes for me is iso-mountings.

This was introduced within Hardy but a "hidden" function.

- Right click on a iso and "Open with" > "Archive mounter".

- The mounted iso appears as a shortcut.


But... it crashes directly for me if I tries to open it.

Bug ?   Can anyone confirm ?  :)

Picture
[[IMG]http://pix.nofrag.com/4/b/d/8a6749e5be45c0d72daf1ca82c018t.jpg[/IMG]]("http://pix.nofrag.com/4/b/d/8a6749e5be45c0d72daf1ca82c018.html")

Mounting archives works but, like you, trying it with an iso crashes Nautilus...

---

### Post by prshah on 2008-08-05
> **Bou said:**
> Hi, you probably know that Nautilus recently got tab support. 

The pathbar buttons now behave like real buttons. 

Am I missing something? I'm running Hardy fully updated, with Nautilus 2.22.3 but I don't seem to have any of these features you mention... or is this some non-repo kind of thingy?

---

### Post by mc4100 on 2008-08-05
> **prshah said:**
> Am I missing something? I'm running Hardy fully updated, with Nautilus 2.22.3 but I don't seem to have any of these features you mention... or is this some non-repo kind of thingy?
From the gnome ftp site, 
[http://ftp.acc.umu.se/pub/GNOME/sources/nautilus/2.23/nautilus-2.23.5.news](http://ftp.acc.umu.se/pub/GNOME/sources/nautilus/2.23/nautilus-2.23.5.news):

> Major changes in 2.23.**5** are:
*** Add tab support to browser mode**
* Add "restore from trash" functionality (only per item)
*** Path bar and notebooks can be used as fully functional URI drop targets**
* Places sidebar
  * Add eject buttons to volumes
  * Fix bookmark reordering
  * Make DND indication consistent with GTK+ file chooser
* Async I/O
  * Use NautilusFile instead of GFile for path bar display name
  * Use NautilusFile for DND "same FS" check
* Fix navigation where window was inconsistently "stuck" between two
  directories, i.e. the view was not completely changed.
* Fix huge leak - status bar messages were never popped from the stack
* Always grab focus on location change, even if view is reused
* Icon view fixes
  * If no icon is selected, but an icon has the keyboard focus, select it when
    pressing space.
  * Move keyboard focus after a file has been removed
  * Fix double-clicking of half-shown items
* Thumbnailing changes
  * Never scale up any thumbnails
  * Compose and scale thumbnails on the fly
  * Speed up loading of large image files used as their own thumbnails
* Display emblems for small icon sizes
* Offer clipboard contents as text/uri-list
* Use UTF-8 dash for properties window instead of "--"
* Misc
  * Allow to build without XMP
  * Require beagle 0.2.4
  * Require intltool 0.36.3.

---

### Post by Gina on 2008-08-05
> **amano said:**
> Just don't middleclick something and it is the old way then? And you can even turn off the behaviour in gconf.Best of both worlds :)

---

### Post by BwackNinja on 2008-08-05
Navigational nautilus is much improved and now it seems everything works smoothly with major changes, but spacial nautilus is nice too. IMHO, everyone should try it at least once.

---

### Post by yellerKat on 2008-08-05
Just applied recent updates - nautilus now supports NFS drives! Party time!

---

