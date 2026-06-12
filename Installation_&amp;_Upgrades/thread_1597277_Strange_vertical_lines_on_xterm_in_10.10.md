---
title: "Strange vertical lines on xterm in 10.10"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by toadwarble on 2010-10-15
I have just upgraded to 10.10 and whilst most things are running OK so far I've noticed a funny quirk with xterm in that when it starts up at first the things I type get displayed with funny lines round them.

(I have had a series of Desktop entries for years corresponding to remote systems I often connect to all of which have xterm in - I have different backgrounds for each to remind me what system I'm talking to).

This is regardless of what font I specify.

If I do any resizing or change the font and then change it back, the problem goes away.

An example follows - maybe I should just switch to Eterm or something?

[IMG]http://www.john.collins.name/sshot.png[/IMG]

---

### Post by finarf on 2010-10-20
I can confirm that I have the same bug. I am using xterm with the lucidasanstypewriter font.

---

### Post by t85us on 2010-10-20
here the same problem..

---

### Post by Sodki on 2010-10-21
This is especially annoying for me because ClusterSSH uses xterm by default and I have to use ClusterSSH a lot.

---

### Post by TopicMapper333 on 2010-10-21
I have the same problem.  The vertical lines are the residue of the cursor.  Since my cursor is red, I have red lines.  This is not a problem in 9.04, 9.10, or 10.04.  Only in 10.10.

---

### Post by lminier on 2010-10-21
See bug [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/635258](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/635258)
fixed in Ubuntu development tree (natty), pending in maverick

---

### Post by finarf on 2010-10-22
> **lminier said:**
> See bug [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/635258](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/635258)
fixed in Ubuntu development tree (natty), pending in maverick

Fixed after downloading the compiz binary. Thanks!

---

