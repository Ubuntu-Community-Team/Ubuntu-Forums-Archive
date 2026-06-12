---
title: "[SOLVED] Intrepid Ibex"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Andrew79 on 2008-10-12
If I do the upgrade to 8.10 via the terminal what is the command and also, will it keep all my files and settings and stuff that takes days to get set back up again the way you want?

---

### Post by Delvien on 2008-10-12
> **Andrew79 said:**
> If I do the upgrade to 8.10 via the terminal what is the command and also, will it keep all my files and settings and stuff that takes days to get set back up again the way you want?



sudo do-release-upgrade


It will keep your files, and most of your configs (some things have changed)

---

### Post by Sef on 2008-10-12
1) Moved to Ibex Forums.

2) >  sudo do-release-upgrade

That is not correct.  That way is not supported anymore.  Click [here]("http://ubuntuforums.org/showthread.php?t=936696") to read about how to correctly upgrade to Intrepid Ibex.

---

### Post by madmetal on 2008-10-12
better move this discussion and have a look here 
[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

---

### Post by wgrant on 2008-10-12
> **Andrew79 said:**
> If I do the upgrade to 8.10 via the terminal what is the command and also, will it keep all my files and settings and stuff that takes days to get set back up again the way you want?

See [the beta release notes](http://www.ubuntu.com/testing/intrepid/beta) for upgrade instructions. If you upgrade, your files and settings will be retained.

---

### Post by wgrant on 2008-10-12
> **Sef said:**
> That is not correct.  That way is not supported anymore.  Click [here]("http://ubuntuforums.org/showthread.php?t=936696") to read about how to correctly upgrade to Intrepid Ibex.

That is one of the two supported ways. That is meant for X-less systems, but there's little wrong with it for desktop installations.

I repeat: The obsolete ways are using tools such as apt-get or aptitude. update-manager and do-release-upgrade are the supported methods.

---

### Post by Delvien on 2008-10-12
> **wgrant said:**
> That is one of the two supported ways. That is meant for X-less systems, but there's little wrong with it for desktop installations.

I repeat: The obsolete ways are using tools such as apt-get or aptitude. update-manager and do-release-upgrade are the supported methods.

Thank you, I didnt think I was wrong.. :D Sef making me look bad! :o

---

### Post by Sef on 2008-10-13
> [[COLOR=#76482C]**wgrant**[/COLOR]]("http://ubuntuforums.org/member.php?u=57283") That is one of the two supported ways.Thanks for the notice about that.

> [Delvien]("http://ubuntuforums.org/member.php?u=44002")  Thank you, I didnt think I was wrong.. :grin: Sef making me look bad! :eek:     Don't worry it won't end here.  Paranoia is good now.:lolflag:

---

