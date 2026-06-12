---
title: "Ctrl-Alt-Arrow changing terminals"
date: 2010-02-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mr.n.nand on 2010-02-05
Hi,

I am testing Lucid Alpha2, fully updated. 
The keyboard shortcut Ctrl-Alt-Arrow has now started switching terminals instead of letting compiz switch desktops. I was not able to locate where to change this setting. It is not set in Gnome Keyboard shortcuts.

How do I disable this?

Thanks,
Nishith

---

### Post by Jordanwb on 2010-02-05
I tried Ctrl+Alt+Arrow and nothing happens. I used the compiz config manager (apt-get install compizconfig-settings-manager) and set Super+Arrow for changing workspaces.

It seems you're confusing terminals with desktops.

---

### Post by jpeddicord on 2010-02-05
That can happen if you were using the SysRq keys to kill X or something. More specifically, Alt-SysRq-R causes certain keyboard bindings to be mapped back to system defaults, which includes Ctrl-Alt-Left/Right. A reboot will usually fix it (or possibly just a sign out and back in).

---

