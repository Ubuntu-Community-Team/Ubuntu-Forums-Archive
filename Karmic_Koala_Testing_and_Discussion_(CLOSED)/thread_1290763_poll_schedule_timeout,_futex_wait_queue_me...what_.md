---
title: "poll_schedule_timeout, futex_wait_queue_me...what do these mean?"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rifak on 2009-10-13
hey everyone,
in System Monitor under Processes tab and Waiting Channel column, i get these values: poll_schedule_timeout and futex_wait_queue_me and some others. what do these mean? i don't remember seeing these in my 8.04 installation. is this a new column of System Manager all together? or have my eyes just been shut this past year...

---

### Post by VMC on 2009-10-13
I asked the same question [here]("http://ubuntuforums.org/showthread.php?t=1284673")

Very little detail is know about the poll_schedule. I manned top to see if anything there. Just a couple of google posts. It's mystery. But it appears everyone has it.

Maybe if I dug deeper I could find something else, but knowing I'm not alone is comforting enough for the time being.

---

### Post by rifak on 2009-10-13
ahh yes, that does make me feel a little better that others are experiencing this. i'm not sure if its anything big, because i see absolutely no noticeable effect...as far as i can tell, nothing is acting weird or abnormal with this processes.

---

### Post by VMC on 2009-10-13
Its weird because I can't remember ever having seen that poll_schedule_timeout before. Maybe an update to gnome-system-monitor at some point. But I found someone complaining on a Fedora site that they heard strange noise coming from their hard drive and related that poll message to it. That's why I opened my topic.

Later I was able to get top to display it as well.

---

