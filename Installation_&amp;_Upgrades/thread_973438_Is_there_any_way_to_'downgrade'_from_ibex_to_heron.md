---
title: "Is there any way to 'downgrade' from ibex to heron"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by josephellengar on 2008-11-06
... without doing a clean reinstall?  I've just been having too many problems.  And the whole thing about Firefox not running correctly- that's the clincher.  Right now I'm using Konqueror- which doesn't even run flash.  eww.  Any suggestions?  Thanks in advance.

---

### Post by brodiesel on 2008-11-06
good luck finding an answer. i've been contemplating the same thing. i' going to try to reinstall intrepid from the ground up and see if that fixes my problem, and if not, i'll be hoping someone answered this thread so i can do the same thing.

i sure have heard a lot of complaints about the upgrade...

---

### Post by Partyboi2 on 2008-11-06
Unfortunately you would need to reinstall as currently there is no way to roll back a upgrade without everything getting very messy.

---

### Post by shaggy999 on 2008-11-06
There is no way to do this currently. I think the only way you would be able to do this is if Sun released ZFS under the GPL. Then you could just take a snapshot of the file system, run an upgrade, and if it ends up bad return to the snapshot.

I think you can do that right now in Nexenta (OpenSolaris Kernel + GNU Tools + APT Packaging system). I sure wish I could do that in Linux!

---

### Post by josephellengar on 2008-11-06
I found this:
[https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)
I realize the problems, but my computer is so customized that I think it's worth it, and if I'm going to do a fresh install anyway, it might be easier to have a "catastrophic mess" :lolflag:  Does anyone know how I can customize this to do this downgrade?  Thanks you very much.

---

### Post by brodiesel on 2008-11-07
serious caveat: i don't know what i'm talking about.

Why not try backing up /home in either a separate partition or on another drive and then reinstalling fresh? From what very little I understand, this would preserve your personal touches and allow you to cleanly do the rest.

---

### Post by josephellengar on 2008-11-07
> **brodiesel said:**
> serious caveat: i don't know what i'm talking about.

Why not try backing up /home in either a separate partition or on another drive and then reinstalling fresh? From what very little I understand, this would preserve your personal touches and allow you to cleanly do the rest.

Good suggestion, but much of it is installed programs from all corners of the internet, among other things.  You know, stuff that doesn't go into my ~ directory.  Oh well, I think that I'm just going to wait this problem out and take this into consideration next time I decide to upgrade to the next version on the day it  comes out. :(

---

