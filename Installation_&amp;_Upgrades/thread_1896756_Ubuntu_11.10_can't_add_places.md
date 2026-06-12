---
title: "Ubuntu 11.10 can't add places"
date: 2011-12-17
forum: Installation &amp; Upgrades
---

### Post by thorbjornw on 2011-12-17
I have made a clean install of Ubuntu 11.10 on my Vaio VGN SZ750.  In 11.04 everything was working fine.  Now I have two problems:  
1.  The first is that I can't add places or bookmarks in Nautilus.  I can edit the bookmarks, i.e. eliminate e.g. videos, but it still appears there. Neither dragging and dropping or using cltr. D does add a bookmark.
2.  The second is that I can't get suspend to work, with the normal workarounds recommended when googling the problem, as installing Hibernate.  Suspend has always been difficult with this lap-top, but this time I have had to give up.
Any suggestions, or should I just go back to 11.04?

---

### Post by thorbjornw on 2011-12-22
Well I found out how to add places / bookmarks.  I can't drag-and-drop as before, but if I open the file and then go to bookmarks and marks "add" it will be added.  But it is not enough to point to the file, you have to actually open it.  I still can't get rid of the pre-defined bookmarks."Videos"? - I don't have videos on my laptop.  But somebody seems to think I should not be able to delete the bookmark.  When I delete it in the "edit bookmark" it still appears in the left panel. I suppose I will have to edit the nautilus set-up file manually or simply live with these bookmarks.  

I haven't found out yet how to get suspend working.

---

### Post by thorbjornw on 2012-01-10
I finally found a way to get rid of the pre-installed bookmarks:

Open a terminal and type

sudo gedit ~/.config/user-dirs.dirs

Then delete or comment out the unwanted bookmarks.
:P

---

### Post by jaycee23 on 2012-01-16
This is what I was looking for - I will try it when I get home

---

### Post by thorbjornw on 2012-01-16
Well I was too fast chanting victory.  When rebooting the system, the ~/.config/user-dirs.dirs file goes back to the original.  So I still haven't found a way to eliminate the pre-defined places.

---

### Post by Toost Inc. on 2012-05-07
instead of editing ~/.config/user-dirs.dirs you need to edit ~/.gtk-bookmarks. user-dirs handles the user folders, not the bookmarks.

Hope this helped

---

### Post by thorbjornw on 2012-05-07
Not really.  The ~/.gtk-bookmarks file only contains the bookmarks, I have defined myself, not the ones predefined by the system.

---

### Post by cmcanulty on 2012-08-07
in nautilus just rt cl and remove

---

