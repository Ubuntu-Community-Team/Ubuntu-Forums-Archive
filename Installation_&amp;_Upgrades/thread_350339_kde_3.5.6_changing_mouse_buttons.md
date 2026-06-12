---
title: "kde 3.5.6 changing mouse buttons?"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by Rizado on 2007-01-31
Today I found out the new kde 3.5.6 was out and upgraded, everything was just fine until I restarted X (Problably loading kde properly). My mouse buttons are screwed. Middle mouse button have switched place the right and side buttons is no longer working...
I have a logitech mx510 and have used the guide here to make all buttons work. They still report as the right ones in xev but does not do what I want to. Before upgrade everything was just fine.

Any ideas?

---

### Post by Rizado on 2007-02-01
This is terrible. After 24 hours only 13 have viewed this thread :-| Got to be very lucky then.

How and where can I change the mouse behaviour in kde? Because they ARE the right buttons but kde uses them the wrong way. There must be a setting somewhere.

---

### Post by randcoop on 2007-02-02
I don' t know the answer, but suggest you try asking it at [http://www.kubuntuforums.com]("http://www.kubuntuforums.com").

---

### Post by Rizado on 2007-02-02
Okey got everything working again. I *think* I know what the problem was. I had copied a xmodmap config from an old installation because of some special keyboard buttons I had configured. In there were some pointer config that I used to make it work, but with the new installation I have not used the same method. With KDE 3.5.5 that part of the config was skipped because of some strange reason but not with the KDE 3.5.6

Very strange...

---

