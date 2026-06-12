---
title: "Application launcher shortcut not working (Alt +F2)"
date: 2009-09-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hype on 2009-09-02
Hi there,
since a few weeks i've been unable to use the Alt+F2 shortcut to get the application launcher menu.

 I've checked the "Keyboeard shortcuts" menu in system>preferences and the shortcut is actually set to Alt + F2.

I also tried to assignone of my keyboard additional keys without success.

Any ideas ?

Seems like it's been posted on launchpad: [https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/401018](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/401018)

---

### Post by steeleyuk on 2009-09-02
Is the keybinding set in gconf?

/apps/metacity/global_keybindings/panel_run_dialog and check its set to <Alt>F2

---

### Post by taavikko on 2009-09-02
> **hype said:**
> 

Any ideas ?

Seems like it's been posted on launchpad: [https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/401018](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/401018)

So what's the problem?

Just unset solid color from panel background, and it works again.

---

### Post by vulfgar on 2009-09-03
> **taavikko said:**
> So what's the problem?

Just unset solid color from panel background, and it works again.

What exactly do you mean by that? I actually tried to change panel properties but of course it didn't make any differens, so I realize you must have meant something else. :)

---

### Post by steeleyuk on 2009-09-03
I actually tried this yesterday.

Currently, ALT+F2 works. Go to the top panel, change the color to solid. Try ALT+F2... it doesn't work. Change the panel back to using the system theme... ALT+F2 still won't work. Open a terminal, type killall gnome-panel and wait for the panels to reload. Try ALT+F2 again and it should work.

Very strange bug.

---

### Post by vulfgar on 2009-09-03
> **steeleyuk said:**
> I actually tried this yesterday.

Currently, ALT+F2 works. Go to the top panel, change the color to solid. Try ALT+F2... it doesn't work. Change the panel back to using the system theme... ALT+F2 still won't work. Open a terminal, type killall gnome-panel and wait for the panels to reload. Try ALT+F2 again and it should work.

Very strange bug.

Thanks, but it doesn't work for me. :( I'm going to go on trying with all installed themes and see if I can get it to work.

Edit: No, it doesn't work with any theme, and it doesn't matter if Visual Effects are active or not.

Edit 2: Now it works, I forgot to change the lower panel.

---

