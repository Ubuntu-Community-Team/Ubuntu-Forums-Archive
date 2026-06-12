---
title: "Update manager"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by wfp on 2009-03-30
If I use sudo apt-get update from a terminal updates do download but I get nothing in the notification are. I have to open update manager and they are there. Also in update manager I have a greyed out Gstreamer0.10-plugins-bad greyed out.

---

### Post by jocheem67 on 2009-03-30
Same here:

Jaunty 32bit and 64bit on two machines ----- no notification

The CLI does work though...

Another bug is that I have to do "killall gnome-panel" once in a while to get my panel back to live, it random freezes.

An other one: Preferences --- Sound doesn't respond.

---

### Post by wfp on 2009-03-30
Sorry to hear that your having the same problem. I just fixed the problem with the greyed out Gstreamer in update manager by just removing it from synaptic. Other than that one small problem with the notifications jaunty is flying on my machine. Oh I have lock-ups with 8.04,8.10, and jaunty and compiz has always been the culprit for me. If I turn desktop effects off, I never get a lock-up.

---

### Post by Bakon Jarser on 2009-03-30
> **wfp said:**
> If I use sudo apt-get update from a terminal updates do download but I get nothing in the notification are. I have to open update manager and they are there.

It's not broken, it's designed to only notify about securty updates or to notify of other updates once a week (I think that's how it works).  If you want to join the rant about it I suggest you find one of several other threads dedicated to this.

---

### Post by wfp on 2009-03-30
Look no one is ranting I was just asking a simple question no need to get rude.

---

### Post by Bakon Jarser on 2009-03-30
> **wfp said:**
> Look no one is ranting I was just asking a simple question no need to get rude.

I didnt' think you were ranting and I wasn't being rude.  It was just a suggestion.:)

---

### Post by wfp on 2009-03-30
np:)

---

### Post by Basiic on 2009-03-30
What I have been doing is using sudo apt-get update and then using sudo apt-get upgrade so it can install the updates :)

---

