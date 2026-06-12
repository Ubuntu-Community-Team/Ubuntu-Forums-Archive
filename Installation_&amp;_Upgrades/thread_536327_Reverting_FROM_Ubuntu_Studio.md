---
title: "Reverting FROM Ubuntu Studio"
date: 2007-08-27
forum: Installation &amp; Upgrades
---

### Post by cleardensity on 2007-08-27
Hello all - currently I have the latest and greatest version of Ubuntu Studio - however, I am not finding the time to play with all of the neat toys that come with it, and would like to revert back to plain ol' ubuntu 7.04 - is there a simple way of doing this? Would my best bet be to just reinstall from the CD? Will the "upgrade" option on the CD work as far as getting me back to Ubuntu?

Thank you for any help you all can provide!

---

### Post by por100pre1 on 2007-08-27
Try this:

```
sudo aptitude remove ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video && sudo aptitude install ubuntu-desktop
```

Hope this helps. :)

---

### Post by cleardensity on 2007-08-27
eh, it did a bunch of stuff... like removed sound and whatnot, but didn't take away studio or the theme... hrmm.. maybe i did something incorrect? I just copy/pasted your code...

---

### Post by cleardensity on 2007-08-28
I guess noone else has any suggestions or it just isn't possible. 

I am debating on creating another partition, moving all of the files i want to keep to it, and just reinstalling on the original partition... Are there any howto's or tutorials on doing something like this?

Thank you,
:confused:

---

### Post by maybeway36 on 2007-08-28
You could try deleting some hidden dirs in your home directory (i.e. ~/.gnome2) but it might also make some applications' settings go away.

---

### Post by por100pre1 on 2007-08-28
Sorry for the inconveniences, it seems many files were already in use. You can change the looks to the ubuntu defaults manually and then try removing everyhing ubuntustudio with Synaptic.

---

