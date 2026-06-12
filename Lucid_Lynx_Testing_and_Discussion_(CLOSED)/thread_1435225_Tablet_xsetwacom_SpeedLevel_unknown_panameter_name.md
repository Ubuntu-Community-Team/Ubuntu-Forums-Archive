---
title: "Tablet: xsetwacom SpeedLevel unknown panameter name"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ola on 2010-03-21
In Karmic I could change the speed of the pen on the tablet using the *SpeedLevel* and Accel options but in Lucid this option doesn't work.

Here is what I did in Karmic
```

xsetwacom set '"Wacom Graphire4 6x8"' SpeedLevel 5
xsetwacom set '"Wacom Graphire4 6x8"' Accel 7

```

If I run that in Lucid I get the following:
```

$ xsetwacom set '"Wacom Graphire4 6x8"' SpeedLevel 5 && xsetwacom set '"Wacom Graphire4 6x8"' Accel 7
Unknown parameter name 'SpeedLevel'.
Unknown parameter name 'Accel'.

```

How can I change the speed and acceleration for the tablet?

---

### Post by ola on 2010-03-23
It seems like the *SpeedLevel* and *Accel* options are removed from *xsetwacom*.

From what I understood you are supposed to use the speed adjustments in *X* instead. I was pointed to checking out: *xinput --list-props* but I haven't had a chance to try it yet.

---

