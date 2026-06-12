---
title: "Removeing/upgrading packages with apt?"
date: 2007-03-16
forum: Installation &amp; Upgrades
---

### Post by steevk on 2007-03-16
Hey guys-

I have an Ubuntu install here that's acting odd...wine was installed with apt-get, and I wanted to remove it and install the newest one. Problem is, apt says the package is uninstalled, but it doesn't do it.

Any ideas? I've never had this happen before...

---

### Post by yabbadabbadont on 2007-03-16
Why do you think that the program is not uninstalled?  If it is because there is still a .wine directory in your home directory, that is normal.  That directory was not included in the install of wine, but created after, so it won't be removed.  If that isn't your issue, then did you remember to include the "--purge" option when you removed wine?

---

### Post by steevk on 2007-03-16
It's because when I run 'wine --version' is still reports 'wine-0.9.30'

I know that the .wine folder should still exist...

You need to 'sudo apt-get remove wine --purge'? I've not heard of that option...what's the difference.

---

### Post by yabbadabbadont on 2007-03-16
Short answer, it removes any configuration files that get installed.  Normally, they get left behind.

Long answer, "man apt-get"  :D

If "wine --version" still works, I would guess that you might have installed wine at one time using some other method than apt.  Did you?  Compiled from source maybe?  Just guessing here.  If you run "which wine", where does it report the wine executable to be?

---

### Post by steevk on 2007-03-16
I did a cursory scan of the manpage and didn't see anything...maybe my reading comprehension needs work ;). Thanks for the info, I'll look into it more later...

I was told that it was never installed from source...which wine tells me that it's in /usr/local/bin.




After poking around some more, apparently the new wine is getting installed in /usr/bin. So if I move the old wine out of /usr/local/bin, it can't find the new one...how do i change it to look at /usr/bin for wine? Is it something with 'alternatives'? Sounds famillar to me, but I don't know why...

---

### Post by yabbadabbadont on 2007-03-16
> **steevk said:**
> I did a cursory scan of the manpage and didn't see anything...maybe my reading comprehension needs work ;). Thanks for the info, I'll look into it more later...

I was told that it was never installed from source...which wine tells me that it's in /usr/local/bin.

/usr/local/bin almost certainly means that it was compiled from source...  ;)

---

### Post by steevk on 2007-03-16
Weird. I was told that it wasn't...this is actually a friend's computer, not mine. How do I go about fixing it anyway?

---

### Post by yabbadabbadont on 2007-03-16
Either manually hunt down all the files and delete them, or go to the directory containing the source code from which it was installed and run "sudo make uninstall".

---

### Post by steevk on 2007-03-16
The old files are deleted....

```
% which wine
/usr/local/bin/wine
% sudo rm /usr/local/bin/wine
% wine --version
bash: /usr/local/bin/wine: No such file or directory
% cd /usr/bin
/usr/bin/% ./wine --version 
wine-0.9.32
/usr/bin/% cp -l /usr/bin/wine /usr/local/bin/wine
/usr/bin/% cd && wine --version
wine-0.9.30
```

I don't get it.





EDIT: Okay, so after poking around on his computer, apparently he did install it from source....even though he swears he didn't. This has fixed the immediate problem, but I still don't get why what happened above was happening, and how I would fix it if that was the problem...

---

