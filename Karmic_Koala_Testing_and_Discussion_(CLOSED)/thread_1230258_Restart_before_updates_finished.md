---
title: "Restart before updates finished"
date: 2009-08-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-08-03
I've been seeing this alot.

A window pops up asking whether to restart or not before the updates have even finished. Usually, there is still a question regarding whether to remove or keep some packages. But the restart window is already there.

---

### Post by ranch hand on 2009-08-03
I had some trouble with that weeks ago, A1 I think, haven't since.

---

### Post by phenest on 2009-08-04
As you can see, Update Manager is still in the 'Clean up' stage of processing updates, but there is a 'Restart?' window already there.

---

### Post by MacUntu on 2009-08-04
On the bright side it would only abort package removal and not package installations but it's indeed not how it should work.

---

### Post by phenest on 2009-08-04
Reported: [bug 409002]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/409002")

---

### Post by taavikko on 2009-08-04
Added some info, had to enable the update-manager to see if I get the same issue.
now just waiting for some packages to be upgraded that creates the /var/run/reboot-required file and calls for it.

---

