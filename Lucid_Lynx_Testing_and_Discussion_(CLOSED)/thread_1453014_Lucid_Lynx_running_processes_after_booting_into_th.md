---
title: "Lucid Lynx running processes after booting into the OS."
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Paradox Uncreated on 2010-04-12
Is there any information on these, and which does what?

I would like to write a script for intelligent renicing, where that can be done, to avoid jitter, in frameplayback.

Currently I'm doing 

[B]for user in `cat /etc/passwd | cut -d: -f1`; do
      renice -n 14 -u $user;
done[/B]

This results in ofcourse, that services running after booting into X, are niced to 14, and application run by the user, run as normal. Which gives some smaller jitter.

However, this is just my first try. Maybe better results can be achieved with a bit more knowlede of what the processes do and so forth.

Peace Be With You.

---

