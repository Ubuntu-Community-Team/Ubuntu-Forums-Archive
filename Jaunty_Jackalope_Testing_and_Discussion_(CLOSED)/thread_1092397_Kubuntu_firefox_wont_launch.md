---
title: "Kubuntu: firefox wont launch?"
date: 2009-03-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by forcecore on 2009-03-10
i downloaded ff3 from offical site but i cannot run run-mozilla.sh, with ubuntu i can but kubuntu cannot (Alpha 5) ?.

NB: do not recommend some install things because i want use it as portable.

---

### Post by quickshade on 2009-03-10
run it from terminal and see what it outputs.

---

### Post by forcecore on 2009-03-10
i dragged run-mozilla.sh to console and it shows cannot execute (permission is executeable). ubuntu 8.10 works fine with gnome.

---

### Post by forcecore on 2009-03-16
bump kubuntu 9.04 still has same problem (daily 16) that firefox do not launch ?

---

### Post by nyarnon on 2009-03-16
> **forcecore said:**
> bump kubuntu 9.04 still has same problem (daily 16) that firefox do not launch ?

I have the same problem under ubuntu solved it by symlinking

/usr/lib/firefox-3.1b3/firefox-3.1 to /usr/bin/firefox

Everything works like a charm.

---

