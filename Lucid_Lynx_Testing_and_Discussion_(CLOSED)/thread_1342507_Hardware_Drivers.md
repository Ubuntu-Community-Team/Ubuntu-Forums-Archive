---
title: "Hardware Drivers"
date: 2009-11-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by williejones on 2009-11-30
When selecting system, administration, hardware drivers nothing happens?

---

### Post by RAOF on 2009-11-30
Yes.  And?

(If you run it in a console, you'll see that it's mis-handling some policykit messages)

---

### Post by Kevbert on 2009-12-01
Are you connected to the web ?
In terminal you may need to do a 
```
sudo aptitude update
``` or you may need to enable backports under Updates in Software Sources.
What hardware are you trying to get drivers for ?

---

### Post by VMC on 2009-12-01
> **RAOF said:**
> Yes.  And?

(If you run it in a console, you'll see that it's mis-handling some policykit messages)

What's the purpose of having an icon at "System > Admin > Hardware Drivers", if it does nothing!?

---

### Post by 23meg on 2009-12-01
> **VMC said:**
> What's the purpose of having an icon at "System > Admin > Hardware Drivers", if it does nothing!?

Debugging it, reporting / fixing bugs so that it actually *does* the thing it's supposed to do.

This is the development branch, remember? Things can fail at any time. The whole point is to fix them before release.

---

