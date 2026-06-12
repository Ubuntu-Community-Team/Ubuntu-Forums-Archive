---
title: "Kubuntu Update Problem"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by Denizen08 on 2007-12-30
I've been using ubuntu since 7.04 and has upgraded successfully to 7.10, and so far has been satisfied with it. But as the curious cow I am, I went and got myself kubuntu 7.10 to try it out. I used the live CD to install it without a hitch and began tweaking and installing the stuff I want, but as I tried to update from adept everything came tumbling down.

After the update kubuntu wont start anymore and gives me an error message as grub tries to boot it up. Similar problems happen when installing restricted drivers as well (nVidia Geforce 5 driver), but in this case it boots up but never finishes... my desktop hangs just before the log on screen in pitch black; not even the keyboard works which means its not just a display problem.

Concerning the update problems... is there a way to update kubuntu without messing up the system?

---

### Post by Denizen08 on 2007-12-31
I think I found the problem with adept: It doesn't recognize/use the command "--configure" which (I think) tries to look for dependencies not found in the system the package is being installed into. In the end adept cancels the installation mid-way leaving the changes made during installation, causing errors to the system. This is dangerous 'cause if it happens during kernel update (like what happened to me) the repercussions can be fatal. 
 
 Hope this can be fixed in an update if not in the next release of k/ubuntu.

---

### Post by slugvision on 2008-02-08
im having the same problem.......how are ppl using kubuntu then if its like that?
beccause i really want the KDE enviroment

---

