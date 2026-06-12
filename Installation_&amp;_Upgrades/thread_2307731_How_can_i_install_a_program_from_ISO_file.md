---
title: "How can i install a program from ISO file ?"
date: 2015-12-28
forum: Installation &amp; Upgrades
---

### Post by cuong4 on 2015-12-28
Is there a way to do that ?

---

### Post by deadflowr on 2015-12-28
Like from the livecd?

You can add it as a repo.

Open the program Software and Updates, go to Other Software and click Add volume at the bottom.

I think, though, that it looks for a cd/dvd, if it's just a file iso on the system you might need an [isomounter]("https://help.ubuntu.com/community/MountIso").

---

### Post by MAFoElffen on 2015-12-28
Doing that assumes that the package you are looking for and all it's dependent packages are on that CD and organised in a manner that supports being accessed as a local Repo. The LiveCD (itself) is very limited in what it has on it ans assumes that you have an internet connection to the internet for anything that is not on it.

The old "Alternate Install CD" used to be set up this way, which is no longer available for current versions of Ubuntu. The Min Install CD is setup this way for a limited Repo. For "more" these days, you might have to create a local repo yourself (Create your own local reposity), using a method similar to Answer #14 here:
[http://askubuntu.com/questions/3576/how-to-make-usb-drive-as-local-repository](http://askubuntu.com/questions/3576/how-to-make-usb-drive-as-local-repository)

This may be a good idea if you do a lot of installs and do not always have an internet connection. Or need to install wifi drivers, before you can get access to the internet...

---

