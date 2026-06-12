---
title: "Saving Home Using Live CD"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by Dug Fin on 2008-08-06
I have decided that my installation of Ubuntu was hopelessly corrupted during the upgrade from 7.10 to 8.04 and that the easiest way to get going again is to save the contents of the home folder and re-install. I want to save my settings, bookmarks, etc.

I cannot access these running normally (they disappear when I click on them and the images and such on the desktop vanish) or in failsafe mode for some reason. Maybe I could in command line but I would need help with that. I was attempting to copy the contents of home while running from the Live CD but the most important files won't copy because it says I'm not the owner.

Is there a way that I can take ownership of the whole contents of the home folder from the Live GUI? Any other hints?

---

### Post by scragar on 2008-08-06
press alt+F2
type ```
gksu nautilus
```
copy away.

---

### Post by pytheas22 on 2008-08-06
Where are you trying to copy them to--a USB drive, another hard drive partition, another hard drive?

If you want to get around the permissions problem, try opening the file browser on the live CD as root--press alt-F2 and enter in the box:
```

gksudo nautilus
```

and you'll have full permissions (be careful not to damage anything on your hard disk that hasn't been damaged already).

If that doesn't work, you could backup /home from the command-line using a tool like rysync or just plain old cp.  But hopefully running Nautilus as root will solve your problem.

---

### Post by Dug Fin on 2008-08-07
Well Nautilus as root was not as easy as hoped. After opening the file the permissions had to be changed manually but at least it could be done with root privileges.

It seems that it's not going to be easy as I am having to change and move many files individually. The permissions has a button that says it will change all sub folders and files, but that dosen't seem to work for some reason. I am just going to have to take it easy.

Thank You all for your help!

---

### Post by pytheas22 on 2008-08-08
I'm glad you found a way to get it to work, if painfully.

Sometimes Nautilus can be buggy.  If you want to change the permissions on all the files so that you can copy them over more easily, try this command:
```

sudo chmod -R 777 /media/sda1/home
```

(I'm not sure what the path to the directory that you're trying to copy is; if it's not /media/sda1/home, then of course change the command above as needed...Nautilus should show you the path when you're looking at the folders graphically).

That should work better; if you need more guidance let me know.

---

### Post by Dug Fin on 2008-08-08
I figured it out some more. I was having problems because I was opening a second nautilus window that was not root and trying to copy from the root nautilus window to a non-root window. That won't work. I tried doing the copy all within the root window and that did work.

---

