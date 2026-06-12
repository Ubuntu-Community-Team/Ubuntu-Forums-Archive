---
title: "Upgrade of running applications"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by rlbutler on 2008-07-03
How does Ubuntu, I guess update-manager in particular, perform the upgrade of running applications?  For instance xorg and compiz - I think these are ones that it prompts for a reboot after.  Does it install to an alternate path, wait until the reboot sequence for the install, or what?  It was my impression from some work with linkers, loaders, and libraries on other systems that they don't always take kindly to being replaced while in use.


Thanks,
Roy

---

### Post by Pumalite on 2008-07-03
Never had a problem that couldn't be resolved quickly. You might have to reinstall a video driver or restart compiz, but is totally workable.

---

### Post by rlbutler on 2008-07-04
> **Pumalite said:**
> Never had a problem that couldn't be resolved quickly. You might have to reinstall a video driver or restart compiz, but is totally workable.

Sure - it works great.  Just wondering if precautions are taken for running software, like a boot-up install or sym-linking to an alternate path.  I'd like to understand the internals.  If any and all executables and libraries can be replaced at any time, whether running or not, without adverse effect, that would be interesting to know, too.

The files changing underneath lazy loading in the Linux model, locked files in the Windows model, or the time I tried to upgrade the C libraries in place on Irix (and paid the consequences) makes me wonder...


Roy

---

### Post by Pumalite on 2008-07-04
[http://www.ubuntugeek.com/tag/ubuntu-hacks/](http://www.ubuntugeek.com/tag/ubuntu-hacks/)
[http://www.linux-tutorial.info/index.php](http://www.linux-tutorial.info/index.php)
[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)
[http://howtoforge.com/taxonomy_menu/1/1/50](http://howtoforge.com/taxonomy_menu/1/1/50)
[http://www.littleigloo.org/tutorial.php3](http://www.littleigloo.org/tutorial.php3)
[http://www.geekgirls.com/](http://www.geekgirls.com/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)

---

### Post by rlbutler on 2008-07-07
> **Pumalite said:**
> [http://www.ubuntugeek.com/tag/ubuntu-hacks/](http://www.ubuntugeek.com/tag/ubuntu-hacks/)
[http://www.linux-tutorial.info/index.php](http://www.linux-tutorial.info/index.php)
[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)
[http://howtoforge.com/taxonomy_menu/1/1/50](http://howtoforge.com/taxonomy_menu/1/1/50)
[http://www.littleigloo.org/tutorial.php3](http://www.littleigloo.org/tutorial.php3)
[http://www.geekgirls.com/](http://www.geekgirls.com/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)

That's plain silly.  There is depth to the question.


Roy

---

