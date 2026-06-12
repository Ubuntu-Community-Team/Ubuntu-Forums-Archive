---
title: "Cannot access unmounted HDD partitions from Live session"
date: 2017-09-20
forum: Installation &amp; Upgrades
---

### Post by The Bright Side on 2017-09-20
Hey guys! I'm installing Ubuntu on a new laptop. I planted the 2 TB hard drive from my old laptop in it, which has all my data on it.

Usually, when I reinstall Ubuntu, I boot into a live session and then use *sudo nautilus* to mount the partition that has my home folder on it, then delete all the user stuff (all the hidden folders) from the home folder. That way, I can start with a fresh Ubuntu, but keep all my files.

Only this time, my unmounted partitions simply won't show up in Nautilus when I launch it in a live session!

How do I get to them?

(additional info: I already installed Ubuntu and found all my old settings still in place, then facepalmed and restarted a live session to delete that stuff, intending to do a clean and fresh re-install after that. This is how I got to where I am now.)

---

### Post by The Bright Side on 2017-09-20
The partitions:

[www.ouimingle.com/imgs/gparted.jpg]("www.ouimingle.com/imgs/gparted.jpg")

The one I'm trying to access is the one with the mouse cursor on it.

In Nautilus, I see this:

[www.ouimingle.com/imgs/nautilus.jpg]("www.ouimingle.com/imgs/nautilus.jpg")

I am used to seeing unmounted partitions in the sidebar or in the "Other Locations" area. But this time, nada. :-/

(I tried putting these pictures inline here but it wouldn't work).

---

### Post by The Bright Side on 2017-09-20
SOLVED!

Took me some searching, but I got the solution:
[http://gparted-forum.surf4.info/viewtopic.php?id=17006](http://gparted-forum.surf4.info/viewtopic.php?id=17006)

---

