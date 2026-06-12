---
title: "multi head xorg.conf with equal screens"
date: 2006-02-20
forum: Installation &amp; Upgrades
---

### Post by zz_miguel on 2006-02-20
Hi

I got multi-head xorg.conf with xinerama working fine on my laptop. The card is an intel 855.
But I want both screens working, showing the same image.
As a workaround, I configured sencod screen with a relative position of 0,0
from the first one. 

        Screen          0 "Default Screen" 0 0
        Screen          1 "Screen2" Relative "Default Screen" 0 0


It does more or less what I need, but I have no cursor on
the second one. And I can not move focus to the second one to change
resolution using ctrl alt + 

Any idea?

thanks in advance


Miguel

---

