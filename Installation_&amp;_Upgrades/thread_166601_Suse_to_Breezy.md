---
title: "Suse to Breezy"
date: 2006-04-26
forum: Installation &amp; Upgrades
---

### Post by jdieter on 2006-04-26
I have a SUse box. I want to save all the /home/ and /www and such - but upgrade the box to BB.
Can I just stick in the Beezy cd and boot from it? Will it save all my config etc??
Or do I need to tar up all the files and webs and mysql db's etc... and then restore tham all after BB is installed?

---

### Post by vigos on 2006-04-26
I would say it depends on how you have your SUse box partioned. Are /home and /www on actual partions? If so I'd say it should be possible to instally Breezy and keep this data

---

### Post by Sef on 2006-04-26
> I have a SUse box. I want to save all the /home/ and /www and such - but upgrade the box to BB.
Can I just stick in the Beezy cd and boot from it? Will it save all my config etc??
Or do I need to tar up all the files and webs and mysql db's etc... and then restore tham all after BB is installed?

1) First **back up** all your files.  If you save /home, you should have them, but if something happens, you will be able to put them back on.

2) To save home, don't delete or change anything in it, when partitioning (do it manually.)

3) Don't know how to save www files.

4) Just make sure that your computer is set to boot from the cd-rom first.  Then put in the install disk and it will be detected.

---

### Post by jdieter on 2006-04-26
Its one big root and a swap.
But, ubuntu puts all the packages and stuff in different places. So, the suse /srv/www/htdocs on ubuntu is /var/www
this is specified in the apache2 conf file. If the ubuntu install preserves all my conf files - is the question. But, you know, I may not want my files in the "suse" place. I just have no idea what the best thing to do is when upgrading from some other distro?

---

### Post by Sef on 2006-04-26
> Its one big root and a swap.

**Back up** everything you want to save.  / will be written over on an install.

---

### Post by jdieter on 2006-04-26
Thanks. That's what I thought would be best.

---

### Post by Sef on 2006-04-26
You're welcome.  If you have any more questions, please post them.

---

### Post by dicecca112 on 2006-04-27
being someone who went from suse to breezy, just backup your bookmarks from firefox by exporting them from within manage bookmarks, and save all your files from Home to somewhere else, in my case a thumbdrive.  You won't be disappointed with Ubuntu its so much better than suse

---

