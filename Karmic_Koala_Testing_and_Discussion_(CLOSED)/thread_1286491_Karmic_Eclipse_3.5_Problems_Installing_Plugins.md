---
title: "Karmic Eclipse 3.5 Problems Installing Plugins"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Drood on 2009-10-09
Hi, when I try to install the Visual Editor plugin in Ubuntu 9.10 + Eclipse 3.5, I get the following error : 

[http://ubuntu.pastebin.com/m66238ade](http://ubuntu.pastebin.com/m66238ade)

I do not know what to do about it, I was also having problems clicking on buttons, a post below this one helped me out with that (tab + enter). Does anyone know what I can do to fix this ? Is it possible one of you guys can make a zip or rar with those files from a previous installation and hand them over ?

---

### Post by Drood on 2009-10-09
A lot of websites suggest it could be a permission error, but running eclipse with sudo produces the same errors, and other people have tried doing chown on the features folders and same thing happens.

---

### Post by Joe_Bishop on 2009-10-09
Man, if you use eclipse from repos -- use plugins from repos.

---

### Post by Drood on 2009-10-09
I tried looking for the visual editor on the synaptics package manager but did not find them. Does it have a less obvious name ? If so please let me know. Thanks

---

### Post by TrueTom on 2009-10-09
> **Drood said:**
> I tried looking for the visual editor on the synaptics package manager but did not find them. Does it have a less obvious name ? If so please let me know. Thanks

Most of the plugins aren't in the repo. It's usually better to just use the Eclipse version from eclipse.org.

---

### Post by Drood on 2009-10-09
I downloaded the eclipse version and it works fine, but then when trying to add  [http://download.eclipse.org/tools/ve/updates/1.4/](http://download.eclipse.org/tools/ve/updates/1.4/) to the list of plugins it says it failed because of missing dependencies :

> Cannot complete the install because one or more required items could not be found.
  Software being installed: Visual Editor 1.4.0.v20090826-1446-777N-CcNBC0BwNk5HZZk (org.eclipse.ve.feature.group 1.4.0.v20090826-1446-777N-CcNBC0BwNk5HZZk)
  Missing requirement: Visual Editor for Java Foundation Classes 1.4.0.v20090826-1446 (org.eclipse.ve.jfc 1.4.0.v20090826-1446) requires 'bundle org.eclipse.gef [3.2.0,4.0.0)' but it could not be found
  Cannot satisfy dependency:
    From: Visual Editor 1.4.0.v20090826-1446-777N-CcNBC0BwNk5HZZk (org.eclipse.ve.feature.group 1.4.0.v20090826-1446-777N-CcNBC0BwNk5HZZk)
    To: org.eclipse.ve.jfc [1.4.0.v20090826-1446]

---

### Post by Drood on 2009-10-09
I'm trying to research on how to get this stuff. If anyone knows please let me know, thanks.

---

### Post by Drood on 2009-10-09
W00T  [http://download.eclipse.org/tools/gef/updates/releases/](http://download.eclipse.org/tools/gef/updates/releases/)

Installing now.

---

### Post by Drood on 2009-10-11
I am still having trouble with this, can anyone offer any solutions to this ? (bump).

I tried downloading versions from eclipses website and it didn't work. I can not even get me to install any plugins now.

---

### Post by guzzi333 on 2009-10-12
I've got the same/similar problem. I downloaded eclipse 3.5 from eclipse.org (as the one in the repos does not allow you to install plugins). When ever I install a plugin it installs to about 60% and after that it just consumes 100% CPU and does not finish

---

### Post by Drood on 2009-10-20
I downloaded eclipse 3.6 and that worked, even though it has not been released yet.

---

