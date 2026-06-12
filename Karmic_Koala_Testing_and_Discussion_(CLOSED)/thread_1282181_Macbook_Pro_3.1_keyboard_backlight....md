---
title: "Macbook Pro 3.1 keyboard backlight..."
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hanzomon4 on 2009-10-04
The keyboard backlight for my Macbook Pro 3.1 does not work when I try adjusting it via the hotkey.. The keyboard backlight is supported however and works! if I manually write to a particular file.

```
echo 255 | sudo tee -a /sys/class/leds/smc::kbd_backlight/brightness
```

I want to file a bug about this but I can't.. Launchpad won't let me.

---

### Post by nanomad on 2009-10-04
> **hanzomon4 said:**
> The keyboard backlight for my Macbook Pro 3.1 does not work when I try adjusting it via the hotkey.. The keyboard backlight is supported however and works! if I manually write to a particular file.

```
echo 255 | sudo tee -a /sys/class/leds/smc::kbd_backlight/brightness
```

I want to file a bug about this but I can't.. Launchpad won't let me.

Err, what's wrong with Launchpad? It works fine here.

---

### Post by hanzomon4 on 2009-10-04
Click the report a bug button on the [Ubuntu project page]("https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=&search=Search+Bug+Reports&field.scope=project&field.scope.target=ubuntu")

---

### Post by hanzomon4 on 2009-10-04
Oh well that's dumb you have to use a super special no redirect url to report a bug... They need to change the name of that button.

[https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect]("https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect")

[EDIT: Bug Report]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/441989")

---

