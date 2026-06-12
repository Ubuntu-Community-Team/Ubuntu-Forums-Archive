---
title: "Unable to find expected entry  universal/binary-i386/Packages in Meta-index file"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by wayneschutz on 2010-01-02
I'm trying to upgrade from 8.04 to 9.10 via 8.10 etc.  When I run update manager, I get this:

W:Failed to fetch [http://ubuntu.media.mit.edu/ubuntu/dists/intrepid/Release](http://ubuntu.media.mit.edu/ubuntu/dists/intrepid/Release)  Unable to find expected entry  universal/binary-i386/Packages in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

and then it closes.  I've unselected all the third party packages and tried various servers, but no difference.  I can wget the file, but when I look at it I see entries for "universe/binary-i386/Release", but nothing for "universal" ...any ideas?

---

### Post by wayneschutz on 2010-01-03
thoughts, anyone?  I tried searching everywhere for this message, but no useful hits.:confused:

---

### Post by byStanderone on 2010-01-03
...a bit curious why you are upgrading hardy via intrepid, instead of hardy itself.

---

### Post by wayneschutz on 2010-01-03
> **byStanderone said:**
> ...a bit curious why you are upgrading hardy via intrepid, instead of hardy itself.I'm not trying to upgrade Hardy, I'm trying to get to Karmic.  It's my understanding that I can do that by using the upgrade tool to go to Intrepid, then Jaunty and then finally Karmic.  I know I can wipe everything out and install Karmic directly, and maybe thats better, but I'm trying to avoid having to re-install/configure a lot of stuff like apache, perlmods, mysql etc (since I do development work on the laptop). Thanks

---

### Post by wayneschutz on 2010-01-03
Okay, using the power of "grep -R" if found this line in 
/etc/apt/sources.list

 deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy universal

commenting it out fixed the problem... how did it get there
in the first place?

---

