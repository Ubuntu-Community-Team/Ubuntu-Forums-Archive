---
title: "Edgy Upgrde - Terminal Server issue"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by Tannor on 2006-11-02
HI all,

I recently upgraded to Edgy and everything so far is working great aside from one issue I am having, and might be guessing realted to some video drive but not sure


Whenever I use Terminal Server Client and use RDPV5 to any windows box, I connect fine but after a while it has a hard time refreshing the screen and it like the graphics does not redraw properly, so I have stuck windows all over that cannot be moved, even if I minimize and reopen it is still there

Has anyone seen this or any suggestions?

Thanks

---

### Post by Tannor on 2006-11-02
nm looks like i got it solved


flgrx drivers were not running properly had to resintall and take out composite optioins in xorg.conf

---

