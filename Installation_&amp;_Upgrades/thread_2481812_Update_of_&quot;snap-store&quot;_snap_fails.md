---
title: "Update of &quot;snap-store&quot; snap fails"
date: 2022-12-09
forum: Installation &amp; Upgrades
---

### Post by cearlp2 on 2022-12-09
After doing a normal update of Ubuntu 22.04 from an update notification I receive the following message.
  Pending update of 'snap-store' snap
  Close the app to avoid disruptions (13 days left)
What app are they are referring to?

---

### Post by Holger_Gehrke on 2022-12-09
They are referring to the snap-store. Like all descendant of gnome-software it stays in memory and running even when you close its window (and no, that's not a bug, it's a feature: it's meant to make starting it again faster). Call it from the command line with the option '--quit' or use 'ps' to find out it's process id and use 'kill' on it. Run 'snap refresh' after that and it should update without problems.

Holger

---

### Post by maglin2 on 2022-12-09
Or via GUI: System Monitor - Processes - snap-store - right click 'kill'.

---

### Post by cearlp2 on 2022-12-10
Thank you for your responses...
Situation resolved !!

---

### Post by cybrsaylr on 2022-12-10
Thanks. Was wondering about that also.

---

