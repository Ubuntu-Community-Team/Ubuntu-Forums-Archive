---
title: "[SOLVED] 8.10 Update &amp;quot;Error authenticating some packages&amp;quot;"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by N2G(bn#7+ on 2008-10-30
Hi, 

Just trying to follow the normal instructions for updating from 8.04 to 8.10. The Update Manager gives me this error:

"Error authenticating some packages
It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages."

...and then appears to print a list of every package I have installed. 

Can't get beyond there - have tried several times, changing servers, logging out and back in again, etc.

Any help? I'd really like to upgrade today.

---

### Post by martrn on 2008-10-30
Check you apt sources list.  Open up a terminal and type:
```

sudo kate /etc/apt/sources.list                     --or--
sudo gedit /etc/apt/sources.list
```

and stick a ## infront of any unofficial repository's.  Ensure the sources.list is your 8.04 list and is not corrupted.

Remove any unofficial packages put there by getdebs, or and similar .deb unofficial packages you have installed.  You would have been informed they might mess up you installations, so remove them as per instructions from them.

Then do :
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get clean
```

And Finally (fingers crossed)

```
sudo apt-get dist-upgrade
```

---

### Post by N2G(bn#7+ on 2008-10-30
Thanks, that worked finally, though it took a lot of fiddling around to remove all the necessary packages.

I guess the lesson here is to use backports rather than getdeb's...?

Cheers,
Erland.

---

### Post by Slayer93 on 2008-11-02
question. HOw are we supposed to know the ones that are unofficial?

*edit*
Nvm... I figured out that you can uncheck them in the Software sources list. Thanks anyways. :D

---

### Post by elderbuy on 2008-11-23
THANK LOADS !!  I had added the below line to my sources list:
   deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) sid main

in order to install a python application, PythonCAD.  Got an error from synaptic about authentication error, but it installed anyway.  The app worked OK, but got notification that there are 671 updates.  When tried to install the updates, got the same results that erlandh got.  Followed your instructions, and it solved the problem.  Only difference is that because it was a python application, I figured that it was not tightly integrated with the system, so did not delete the app, but everything still worked.  Thanks again.

---

