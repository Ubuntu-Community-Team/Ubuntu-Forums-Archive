---
title: "Changing Conky"
date: 2011-04-09
forum: Installation &amp; Upgrades
---

### Post by jordanv0712 on 2011-04-09
Conky currently for me is located underneathe my bottom panel.  I would like to have it placed to the right of my screen but i can't figure out how to change some of the settings.  Can anyone help me!?

---

### Post by ajgreeny on 2011-04-09
Difficult to know in detail, without seeing your current .conkyrc file, but somewhere there should be a section like
```
# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 30
gap_y 50
```
which in this case means the window is bottom right (the uncommented line) and 30 pixels from the screen edge on the right (gap_x) and 50 pixels from the bottom (gap_y).

Play around with the figures until you get it how you want.  You can start and stop conky to make the changes show most easily with the Alt+F2 run dialog and commands **killall conky** and **conky**.

---

