---
title: "Workspace scrolling with mouse wheel"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by spongypants23 on 2009-09-29
Was this disabled in Karmic?

I seem to no longer be able to switch workspaces by hovering my mouse over the desktop and turning my mouse wheel up and down.

Sort of annoying. I don't want to have to use the keyboard shortcuts.

---

### Post by LittleCannon on 2009-09-29
Hi, I had same problems as you.

open gconf-editor and under

```
/apps/compiz/plugins/vpswitch/allscreens/options
```

find "next_button" and give value "Button5", find "prev_button" and give value "Button4"

Viewport switcher should work now

---

### Post by spongypants23 on 2009-09-29
Thanks!

---

### Post by Nickedynick on 2009-09-29
I tried this via ccsm, but for some reason it changes workspace when I scroll inside a window. Has anyone else seen this behaviour?

---

### Post by LittleCannon on 2009-09-29
> **Nickedynick said:**
> I tried this via ccsm, but for some reason it changes workspace when I scroll inside a window. Has anyone else seen this behaviour?

In CCSM, in Rotate Cube>bindings tab disable under mouse options rotate left and rotate right

---

### Post by blur xc on 2009-09-29
> **Nickedynick said:**
> I tried this via ccsm, but for some reason it changes workspace when I scroll inside a window. Has anyone else seen this behaviour?

It does that to me when scrolling inside some windows, depending one where my mouse is.  This was very irritating, and I disabled this feature in ccsm (9.04 btw)...


BM

---

### Post by Nickedynick on 2009-09-29
I loved it when they introduced it by default, I'm not entirely sure what the reasoning is behind removing it. Unless they couldn't decide on how to write a program to disable it only for touchpads...

---

### Post by fancypiper on 2009-10-27
I still can't use the wheel to scroll workspaces in the upgrade. It works with a fresh install!?

---

