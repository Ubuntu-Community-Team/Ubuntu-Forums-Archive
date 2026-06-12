---
title: "left and middle click mapped to the left mouse button after upgrading to 10.10"
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by radios on 2011-01-17
Hi, after upgrading from 10.04 to 10.10 I was getting weird behaviour when left clicking on my compaq presario f700. Clicking on links in my browser would occasionally open a new tab and click on tabs would occasionally close them. It's quite annoying.

I thought it was something wonky with the upgrade so I did a fresh install but I got the same thing. I looked around and found out about xinput. "xinput test 11" would sometimes show a 2 when clicking the left mouse button. I tried "xinput --set-button-map 11 2 0" (zero disables the middle button right?) but now it seems the middle button has taken over the left button completely.

Is there a definite fix for this? I don't even have a middle mouse button. Thanks.

---

