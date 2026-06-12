---
title: "Intrepid upgrade - Weird Bug"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by georgefrankly on 2008-10-31
This morning I upgraded from Hardy to Intrepid, after letting the packages download overnight.

Everything seemed to go smoothly throughout, and my laptop rebooted just fine after the install.  Everything looks good except for 2 things:

1) When I try to open the file browser from the "Places" menu, instead of opening the browser, it opens the folder in Amarok.  Sounds strange, but I swear that's what's happening.  For instance I hit "Places-->Home", and Amarok starts up, and the files in my home folder attempt to play in Amarok.  Maybe the file browser is misconfigured??  How can I fix this?

2) This one is less critical, but it seems all pop-up bubble messages and mouse-over text on the desktop comes up as a black box.  For instance the "connected to wireless network" bubble that usually pops up is there, but is nothing but a black field.

What is the deal here?  Otherwise, it seems everything is functioning just fine.

Thanks for your help!

---

### Post by oldmanpete on 2008-10-31
*1) When I try to open the file browser from the "Places" menu, instead of opening the browser, it opens the folder in Amarok. Sounds strange, but I swear that's what's happening. For instance I hit "Places-->Home", and Amarok starts up, and the files in my home folder attempt to play in Amarok. Maybe the file browser is misconfigured?? How can I fix this?*

This is happening for me too except that it's opening in firefox and displaying my files in an FTP format as webpages. Very odd. Idea's on a postcard please!

---

### Post by ljoslin on 2008-10-31
> **oldmanpete said:**
> *1) When I try to open the file browser from the "Places" menu, instead of opening the browser, it opens the folder in Amarok. Sounds strange, but I swear that's what's happening. For instance I hit "Places-->Home", and Amarok starts up, and the files in my home folder attempt to play in Amarok. Maybe the file browser is misconfigured?? How can I fix this?*

This is happening for me too except that it's opening in firefox and displaying my files in an FTP format as webpages. Very odd. Idea's on a postcard please!

same for me, except it's totem for me!

-=Larry=-

---

### Post by ezekiel000 on 2008-10-31
Mine just asks me for root password for the Home and Bookmark entries in the places menu, is there a fix yet? It's not too much of a problem as I can get to my home dir by opening nautilus from the Computer entry on the places menu.

---

### Post by ljoslin on 2008-10-31
problem solved

[https://bugs.launchpad.net/ubuntu/+s...us/+bug/260492](https://bugs.launchpad.net/ubuntu/+s...us/+bug/260492)

the only thing is I had to follow the directions 6 or so posts down...open nautilus however, I did it from a terminal, then goto the "home" folder and change the properties to open with file browser, that fixed it for me!

-=Larry=-

---

### Post by ezekiel000 on 2008-10-31
Ah ok fixed, all you have to do is set the default program to open folders to nautilus instead of gksu.

Just right click on a folder and select properties, go to the Open With tab and click on the radio button next to Open Folder rather than gksu.

---

### Post by OwnName on 2008-10-31
Thx to ljoslin & ezekiel000.
Like georgefrankly I upgraded overnight, and I got the same stupid home -> amarok behaviour, and was going crazy with Amarok scanning my all harddisks on and on and on endlessly.
Another nice behaviour so far, is Opera lost completely the sound (on Youtube's, for example), while Firefox still have it.
Any idea, tip or tricks?
Thx in advance  ^___^

---

### Post by enque on 2008-10-31
I would just like to mention that this exact weird bug happened with me too, when I upgraded to Intrepid an hour ago.
Right click folder and selecting the correct "open with" setting corrects the bug, but it's still annoying (and strange!) that this thing made it through to the final release.
Whatever caused it, I have no clue.

---

### Post by jlpino on 2008-10-31
The ljoslin's link doesn't work. This is the correct link:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/260492](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/260492)

---

### Post by kaivalagi on 2008-11-01
In summary, the best fix is to edit ~/.local/share/applications/mimeapps.list removing the offending ?.desktop entries against the inode/directory entry.

e.g. from:
```

inode/directory=userapp-baobab-OO53FU.desktop;nautilus-folder-handler.desktop;nautilus.desktop;userapp-nautilus-XXZ2JU.desktop;
```

to:

```
inode/directory=nautilus-folder-handler.desktop;
```

There is no need to go through all the places bookmarked changing the "open with" options

---

### Post by jlpino on 2008-11-01
kaivalagi, I only do it with a folder (my home) and all places works fine.
Anyway, thanks for your solution.

---

### Post by georgefrankly on 2008-11-01
Thanks everyone for your help so far,
but I tried the 'Open with app' --> nautilus, and it is still not working.  If I run nautilus from ALT-F2, I can click on folders and they work fine, but everything in the Places menu still tries to open in Amarok.

according to that link, the problem is with nautilus itself.  can I try to update nautilus to fix the problem?

Also, does anyone have any insight on the mystery of the missing hover-text?  I still just get black boxes on the desktop.

---

### Post by oldmanpete on 2008-11-01
> **georgefrankly said:**
> Thanks everyone for your help so far,
but I tried the 'Open with app' --> nautilus, and it is still not working.  If I run nautilus from ALT-F2, I can click on folders and they work fine, but everything in the Places menu still tries to open in Amarok.

according to that link, the problem is with nautilus itself.  can I try to update nautilus to fix the problem?

run nautilus through alt f2. Browse to your home icon, right click > properties > open with > select open with folder. It should then open normally.

---

### Post by georgefrankly on 2008-11-01
yay thanks!  I are moron.

---

### Post by georgefrankly on 2008-11-04
Does anyone have any insight on my mouse-over text problem?

It still hasn't been resolved and it's sort of inconsistent.  
No mouseover text on the desktop works, but it works in many applications like firefox.

What is the deal?

---

