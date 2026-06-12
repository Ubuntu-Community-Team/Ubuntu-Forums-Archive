---
title: "Notification area garbled on two  machines"
date: 2010-04-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by QwUo173Hy on 2010-04-25
The picture (attached) says it all. Both machines are running Intel graphics and a fully updated Lucid. Anyone else got this?

Basically the wireless indicator is gone, the battery is split in two and it's not possible to log out / shutdown via the gui.

---

### Post by xerosis on 2010-04-25
Yeah I've seen that, it seems to be fixed by a restart and it doesn't happen every time.

---

### Post by andrek on 2010-04-25
Try

```
killall gnome-panel
```

to fix this.

---

### Post by null_pointer_us on 2010-04-25
I got some odd panel problems a while ago due to some updates.

Someone recently posted this...

```
gconftool-2 --recursive-unset /apps/panel
```

```
killall gnome-panel
```

...which worked fine for me.

Note that it resets your panels to the default. Any customizations you made will have to be reapplied. I suppose there's some way to edit the panel properties directly in some text file, but I never looked for it.

---

### Post by QwUo173Hy on 2010-04-25
Thanks xerosis, andrek, null_pointer_us. I did two restarts and didn't see an improvement. But on this (the fourth, I think) boot, it's almost okay again. I'll use the commands posted if it happens again.

---

