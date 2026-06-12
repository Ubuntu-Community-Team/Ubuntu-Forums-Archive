---
title: "Upgrade to Feisty or do a new Install to root partition"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by DrewB on 2007-05-07
Hello,
I currently have Ubuntu Edgy installed with seperate partitions for /, /home, /usr and /opt.

I'm just wondering if it would be better to do a new install of Feisty, rather than an upgrade, so that I get a completely clean and fresh system. I don't mind losing my settings\configuration etc. as long as my programs and home data remain intact.

If I did do a new install of Feisty, presumably I would install it to / and my /home, /usr and /opt directories would be unaffected?

I'm very new to this, Edgy was my first install of Ubuntu so this is the first upgrade of Ubuntu I've ever done.
Thanks a lot for any advice anyone can give.
Andy

---

### Post by hal8000 on 2007-05-07
If you look through the forum you will see many problems related to Feisty especially with the new kernel 2.6.20
If you are a beginner you may have trouble fixing this though there are different solutions which work for many people.

It may be better to keep your existing installation, if it isnt broke, dont try and fix it.  You cant keep /usr and /opt
these will get overridden or become superfluous. AFAIK, the only linux system that upgrades without problems is Debian, but in any case, as k3b or gnomebaker is available I would backup your personal data from /home onto a cd.

Configuration of the desktop doesnt take that long and you dont have to do it all at once.
See what others say about an upgrade, but unless you are able to fix your install should it break, I would advise caution, hope that helps.

---

### Post by sjnovick on 2007-05-07
You're correct.  If you do a new install, only your root "/" partition is overwritten (unless you give express permission to overwrite the others).  All of your settings will be retained.  If you want your settings to be overwritten, the

1.  Open nautilus to your home directory.
2.  View hidden files in your home directory.
3.  Delete the files beginning with "." that correspond with settings that you want overwritten.


I have performed fresh installs and upgrades (as I have multiple computers).  The upgrade took about 1 hour.  The fresh installs took about 3 hours (because I had to re-load all of the software).  There were no glitches either way.  Good luck to you.

---

### Post by DrewB on 2007-05-07
Hi, Thanks a lot for your replies.
If I do a new install over the root partition, would I have to delete the new /opt /home and /usr directories that would be created and then re-mount the old ones (the ones I want to keep) in /etc/fstab, that I have on the separate partitions.
Would this work? Would there be in problems with using my Edgy /opt, /usr and /home partitions with the new Feisty install?
Thanks

---

### Post by Kingsley on 2007-05-07
I did an upgrade from Edgy to Feisty. It took a while but the upgrade was flawless.

---

