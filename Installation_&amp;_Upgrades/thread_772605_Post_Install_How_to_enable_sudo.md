---
title: "Post Install: How to enable sudo"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by supergrover1981 on 2008-04-28
Hi Guys,

I've just tried to upgrade from 7.10 to 8.04. The process was going fine, but while updating chillispot (approx %85...I think) the installer froze.

Upon restarting, most programs were updated and most functionality was fine, apart from a few things:

- Most importantly, trying to run sudo commands brings up "sudo: unable to resolve host linuxlaptop"

- Even fairly basic actions, such as copy/pasting in nautilus, bring up an insufficient permissions notification

- Network manager has disappeared, making internet connections impossible


I suspect/hope I can solve the network manager problems via others' posts on this forum if I can get sudo back - that's the one that's really causing trouble. I tried commenting out the "linuxlaptop" line in /etc/hosts, but it had no effect.

Any suggestions at all deeply appreciated.

Cheers,
        - Supergrover

---

### Post by dioukf on 2008-04-28
Boot from installer CD, mount your filesystem, and edit your etc/sudoers file.

---

### Post by hyperair on 2008-04-28
The /etc/sudoers file is configured correctly by default. The problem here is that the computer cannot resolve its own hostname. What you must do is open System->Administration->Network, go to Hosts, click "Add". IP Address is 127.0.1.1, and type your hostname (i.e. linuxlaptop) under the aliases. 

Alternatively you could open your /etc/hosts file and add this line:
```

127.0.1.1 linuxlaptop

```

Restart and your sudo shall be fixed.

---

### Post by glendavee on 2008-04-28
Have a look at this thread
[http://ubuntuforums.org/showthread.php?t=770883](http://ubuntuforums.org/showthread.php?t=770883)

---

### Post by supergrover1981 on 2008-04-28
*standing ovation*
*rapturous applause*
*throws panties*

...Many thanks guys, worked a charm. Still a whole other bunch of errors I need to work through, but this one makes it all a lot easier. Cheers.

 - SuperGrover

---

