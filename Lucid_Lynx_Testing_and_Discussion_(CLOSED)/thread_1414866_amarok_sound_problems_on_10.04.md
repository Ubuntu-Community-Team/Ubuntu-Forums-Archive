---
title: "amarok sound problems on 10.04"
date: 2010-02-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gwenn on 2010-02-24
I have no sound on Amarok!
I like the new features that Amarok has but I can't make it works.I tried to switch between the various sound configuration that Amarok has but nothing changes, and when I look into the main sound preferences there no application that use the system sound even if amarok seems to play a song!

---

### Post by seeker5528 on 2010-02-24
If Amarok goes through the motions of playing but you don't hear anything I would go through these steps.....

Make sure phonon-xine is installed along with at least libxine1-ffmpeg I usually install libxine1-misc-plugins as well.

Make sure xine is selected as the backend.

If it still doesn't work, then try uninstalling pulseaudio and pulseaudio-* packages.

Later, Seeker

---

