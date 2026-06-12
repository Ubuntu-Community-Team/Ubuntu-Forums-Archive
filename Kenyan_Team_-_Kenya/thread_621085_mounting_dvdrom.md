---
title: "mounting dvdrom"
date: 2007-11-23
forum: Kenyan Team - Kenya
---

### Post by bobzz on 2007-11-23
how do iget to be playing ma dvd's??

---

### Post by ronaldotis on 2007-12-04
I think you ought to have given more details like the dvd device you are running. Anyway, from my experience I think your dvd is not automatically detected so you have to change your fstab.
In the command line after logging in as root cd to /etc/fstab then make sure that the hdc has the following entries:
/dev/hdc auto user,noauto 0 0

Alternatavely, if you do not mind manually mounting it you can run:
mount /dev/hdc /media/cdrom and whenever you are through you use umount to unmount it.

---

### Post by sagarhshah on 2008-01-09
If you can already see you dvds on your desktop but can't play them then you might need the dvd css codec as ubuntu doesn't come with any proprietary codecs like mp3 dvd wmv etc.
I find the best way to install the required media codecs required to play dvds and other video and audio formats is install it using automatix if you have a decent internet connection.

[http://www.getautomatix.com](http://www.getautomatix.com) is the website for it and the instructions to install it are on there and the application is pretty intuitive to use so should be easy to figure out.

Hope this helps
Let me know if you need more help.

---

