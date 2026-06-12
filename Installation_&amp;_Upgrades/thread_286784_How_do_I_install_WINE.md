---
title: "How do I install WINE?"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by void1 on 2006-10-28
Hello and thanks for the help.

How do I install WINE?  I've search the list provided by: "System->Adept Manager Manage Pageages" but did not find WINE listed.

Thanks for the help.

---

### Post by aurimas on 2006-10-28
It is very simple.
In terminal just:
sudo aptitude install wine

I guess wine works only in 32 bit systems.

---

### Post by sawjew on 2006-10-28
You will need to enable universe repositories.

Go to System>Administration>Software Sources

check the box next to "Community maintained open source software (universe)" and any others you want checked

when you close the window it will ask if you want to update, say yes.

Then either use your package manager (Synaptic, Adept) or open a terminal and type in ```
sudo apt-get install wine
```

after wine is installed type in a terminal ```
winecfg
```

this will set up your fake windows directory and you can then install windows software (but not all windows software works)

---

### Post by void1 on 2006-10-28
Thanks for the help, aurimas and sawjew.

For Newbies (like me) who have downloaded the newest version of KUBUNTU, here is how you enable the "universe" package libraries and install "wine":

K Menu -> System -> Adept Manager Mange Packages
Adept -> Manage Repositories
(Right click) "deb  [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) -> Enable
(Right click" "deb-src  [http://us.archive/ubuntu.com/ubuntu/](http://us.archive/ubuntu.com/ubuntu/) -> Enable
Apply
close

Note: you may also want to enable all "universe" items under "Components".  For example you could also add "deb  http://security.ubuntu.com/ubuntu" and "deb-src  http://security.ubuntu.com/ubuntu".

To install "wine":

K Menu -> System -> Adept Manager Mange Packages
(right click) wine -> Request Install
Preview Changes
Apply Changes

K Menu -> System -> Konsole Terminal Program
winecfg

(At this point, I'm just beginning to figure out wine.  So I'll stop here. ](*,) )

Again, thanks for the help.

---

