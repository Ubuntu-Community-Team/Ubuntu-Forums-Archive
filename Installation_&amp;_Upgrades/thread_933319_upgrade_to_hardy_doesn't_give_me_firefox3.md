---
title: "upgrade to hardy doesn't give me firefox3"
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by tomgarvin on 2008-09-29
i just upgraded to hardy heron, but i don't get firefox3.

via synaptic, i've uninstalled (completely) firefox, then rebooted, then reinstalled the base package (firefox) which auto-required firefox-3.0.  i also installed firefox-3.0-gnome-support since i run gnome.  however, when i launch firefox, then check Help>About Mozilla FireFox... i still get Firefox/2.0.0.14.

what's up with that?

i suppose i'd be happy to install firefox from tarball, but i'd like to make the package work.  any thoughts?

---

### Post by Rayaz on 2008-09-29
Have you checked the repositories? Open synaptic and go to repositories. You should have hardy enabled to be able to install firefox 3.

---

### Post by tomgarvin on 2008-09-29
yeah, i know that i needed hardy to get firefox 3... prior to my move to hardy, that firefox update just hung there and wouldn't let me act upon since i hadn't upgraded.

i've checked the repositories, and turned a few more things on in the updates tab (namely pre-release), but that didn't seem to help.  did you have something specific that i should check in the repositories area?

again, i see the firefox-3.0 packages, and synaptic doesn't bark when i install them... it's just after the process, it still launches into firefox-1.0.

i do have a /usr/bin/firefox and /usr/bin/firefox.ubuntu... but they both launch firefox 2.0.

---

### Post by tomgarvin on 2008-09-29
after complete removal of all synaptic firefox packages, i still had /usr/lib/firefox, /usr/bin/firefox, /opt/firefox, /usr/share/firefox and /etc/firefox.  i'm guessing that i sleep-installed firefox from tarball at some point and forgot about it.

i moved all those directories/files to firefox.bak, then reinstalled from synaptic... and everything seems good.  all i had to do was re-symlink /usr/bin/firefox to /usr/bin/firefox-3.0.

hope that helps someone down the line.  :D

---

### Post by Ray-20871 on 2008-11-03
I'm having the same problem.  Before I head down your path, what did you do to your bookmarks, etc. before you removed firefox

---

