---
title: "Pimlico Tasks list lost during Ubuntu upgrade to 11.04"
date: 2011-08-21
forum: Installation &amp; Upgrades
---

### Post by Manoel on 2011-08-21
I was using Pimlico **Tasks** manager with Ubuntu 10.10 [http://pimlico-project.org/tasks.html](http://pimlico-project.org/tasks.html)

Yesterday I did an Ubuntu upgrade and all seemed to go OK, but today when I opened Tasks... my list was all empty! All tasks gathered for many months all lost! :(

How could this happened? Isn't Ubuntu supposed to mantain all configs and personal data? And more important - is there any way I can recover my task list?

Thanks a lot in advance to anybody who can help!

---

### Post by Manoel on 2011-08-21
With a lot of help from a Pimlico mailing-list subscriber I managed to find my task list in /home/[username]/.local/share/evolution/tasks/system/tasks.ics

but now I don't know how can I open them from Tasks.

My Pimlico Tasks version is 0.16. I have also discovered that I haven't Evolution installed. May it be the source of this inability of Tasks to find and recover the former task list? Now with each new session Tasks creates a new subdir at /home/[username]/.local/share/evolution/tasks/ with a number followed by @ and then my machine's name. Inside it, Tasks puts an empty tasks.ics. :confused:

---

### Post by Manoel on 2011-08-21
> **Manoel said:**
> 
My Pimlico Tasks version is 0.16. I have also discovered that I haven't Evolution installed. May it be the source of this inability of Tasks to find and recover the former task list? 

I can read [here]("http://permalink.gmane.org/gmane.comp.handhelds.pimlico/213") the following:

*Tasks uses the system default task list in evolution-data-server*
So I guess that if no Evolution server is present, Tasks could be unable to find the default list and try to create each time a new one. ...I'm just guessing.

---

### Post by Manoel on 2011-08-21
That was the problem! 

After installing Evolution suite from my Ubuntu Software Center, I re-started, re-opened Tasks and then this app was able to find my former tasks.ics!

If someone has the same problem, and it doesn't work, just try to open first Evolution mail & calendar before opening Tasks.

Lessons learned:

1) Ubuntu 11.04 seems not to install Evolution suite.
2) Pimlico Tasks won't be able to find some pre-existent task list, if Evolution not present, and it will create a different one for each new session instead.

Hope this can help someone else.

---

