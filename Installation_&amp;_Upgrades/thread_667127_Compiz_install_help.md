---
title: "Compiz install help"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by Katocan on 2008-01-14
I'm quite new to ubuntu so i don't know much, anyway, I wanted to know how to install compiz so i followed a tutorial, i completely removed compiz to try and reinstall it, but when I try to install compiz-core it says that the package isn't authenticated, how do I get around this problem?

Thanks for any help :)

---

### Post by chewearn on 2008-01-14
Which tutorial are you following?

---

### Post by Katocan on 2008-01-14
The tutorial that i followed was [http://forlong.blogage.de/article/2007/8/29/How-to-install-Compiz-Fusion-on-Ubuntu-Feisty---tutorial-for-advanced-andor-KDE-as-well-as-Xfce-users](http://forlong.blogage.de/article/2007/8/29/How-to-install-Compiz-Fusion-on-Ubuntu-Feisty---tutorial-for-advanced-andor-KDE-as-well-as-Xfce-users)

---

### Post by chewearn on 2008-01-14
It's mentioned in the howto:
> Since the repository doesn't have a [GPG]("http://wikipedia.org/wiki/GNU_Privacy_Guard")-Key, apt will give you a warning, stating »The following packages cannot be authenticated!« - in this case, that's nothing to worry about, but you have to approve this step! Just pressing [Enter] will abort the process.

In other words, just ignore the error, and specifically tell apt to continue the installation.

---

### Post by Katocan on 2008-01-14
Heres a screenshot of synaptic, what should i do from there because if i just hit mark i get another message saying
> compiz:
 Depends: compiz-gnome but it is not going to be installed


so how do i get around this?

Thanks for any help :)

---

### Post by Katocan on 2008-01-14
Anyone got any idea how I could get around this problem then?

---

### Post by Katocan on 2008-01-14
Sorry to bump up the post I'm just wondering if anyone has any idea what the problem could be here and how to avoid it.

Thanks

---

### Post by chewearn on 2008-01-14
Sorry I was off-line.

When I saw your first post, it said you were using Feisty in your profile, but now, you have changed to Gutsy?

The howto you are using is specifically for Feisty.  In Gutsy, compiz is directly available from the ubuntu repositories, and you probably should not have use the external party repo.

See this link, follow part 1 to clean up:
[http://ubuntuforums.org/showthread.php?t=601310](http://ubuntuforums.org/showthread.php?t=601310)

Then, see this link to install compiz in Xubuntu:
[http://ubuntuforums.org/showthread.php?t=623752](http://ubuntuforums.org/showthread.php?t=623752)

---

### Post by Katocan on 2008-01-15
Thanks for the help, I just done a fresh install and it works now :)

---

