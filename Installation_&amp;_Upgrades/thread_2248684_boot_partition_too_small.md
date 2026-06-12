---
title: "/boot partition too small?"
date: 2014-10-16
forum: Installation &amp; Upgrades
---

### Post by RichardET on 2014-10-16
I assumed incorrectly that Ubuntu setup the disk partitions correctly;  now I am running low on /boot space for a new update;

I need to free 74 MB from /boot;  really?  which files can I delete?

---

### Post by Michael_McKenney on 2014-10-16
I used Synaptics to clean up the older Linux-images from Ubuntu.  I kept only 3.13.xx.

---

### Post by slickymaster on 2014-10-16
See this: [How do I free up more space in /boot?]("http://askubuntu.com/questions/89710/how-do-i-free-up-more-space-in-boot")

---

### Post by RichardET on 2014-10-16
Yes thanks, this command worked well:
sudo apt-get purge linux-image-3.0.0-12;  I just replaced the image generations with mine and freed 60% of the 241 MB boot area.

---

### Post by Michael_McKenney on 2014-10-16
Synaptics allowed house cleaning.  I have 30+ revisions that I cleared out.

---

