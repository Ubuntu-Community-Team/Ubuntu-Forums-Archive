---
title: "minimize/maximize boxes on wrong side"
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by bfranky on 2010-12-30
I just upgraded to 9.10 and all the windows for all programs have the minimize/maximize/close boxes on the left side. No big deal, but for decades they've been on the right. Is this something in my computer? If so, can I do something to get them over where they belong?

Thanks much.

Frank

---

### Post by CraigThomas on 2010-12-30
Sorry to be awkward but you say you upgraded to 9.10 and this happened?  I thought they changed the layout for 10.04.  Either way take a look at this it may help:
[http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/]("http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/")

---

### Post by karthick87 on 2010-12-30
Copy paste the following in your terminal,

```
gconftool-2 --set /apps/metacity/general/button_layout --type string menu:minimize,maximize,close
```

---

### Post by pricetech on 2010-12-30
Or just relish the change.  Actually I've gotten quite used to them and keep looking in the "wrong" corner when I'm using a windows box.

---

### Post by trinitydan on 2010-12-30
What if you want to put some of the buttons on one side of the title and some on the other?  Does anyone know a way?  Thanks.

---

