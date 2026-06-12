---
title: "Network Manager Icon in Notification Area turns into Volume Control after reboot"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Muflon on 2009-10-10
Sometimes when I reboot my laptop, the Network Manager icon turns into a a greyed out volume control and doesn't react to being clicked (see attached images).  If I then remove the Notification Area from the panel and then add it back again all returns to normal.

Muflon

---

### Post by taavikko on 2009-10-10
that's not the default icon-set, might be just the icon-set acting up.
If you can re-produce this with the default (Humanity)?

---

### Post by Muflon on 2009-10-10
> **taavikko said:**
> that's not the default icon-set, might be just the icon-set acting up.
If you can re-produce this with the default (Humanity)?

Thanks, I have changed the icons to Humanity as suggested and I will post feedback if the problem reoccurs. 

Muflon

---

### Post by Muflon on 2009-10-10
> **Muflon said:**
> Thanks, I have changed the icons to Humanity as suggested and I will post feedback if the problem reoccurs. 

Muflon

Same problem with different icons.

Muflon

---

### Post by blakamin on 2009-10-10
Mine does it occasionally too.

---

### Post by Jay_Bee on 2009-10-10
I can confirm this, did anyone report a bug?

---

### Post by !nkubus on 2009-10-10
same problems here, sudo killall gnome-panel resolve the issue, but I don't want to have to do this every time.

---

### Post by tekstr1der on 2009-10-10
Yes, I am seeing the same behavior here with breathe icon set. This doesn't happen with every boot. 

```
killall gnome-panel
```

Sets it straight.

---

