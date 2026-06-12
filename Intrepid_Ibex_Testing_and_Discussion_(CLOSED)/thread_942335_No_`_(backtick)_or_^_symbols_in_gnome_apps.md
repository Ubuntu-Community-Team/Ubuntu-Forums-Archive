---
title: "No ` (backtick) or ^ symbols in gnome apps :/"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by danf_1979 on 2008-10-09
Hi guys, I'm using a Spanish-Spanish keyboard configuration, and I'm experiencing a very strange issue. In gnome applications I can't do ` or ^ symbols. I press the keys, and nothing happens, no output. Strangely, I can do this symbols in KDE apps, so I guess this is not an X issue but gnome's.

Anyone has any idea on what could be wrong?

This is driving me nuts, since those symbols are used a lot in bash.

---

### Post by taavikko on 2008-10-09
> **danf_1979 said:**
> Hi guys, I'm using a Spanish-Spanish keyboard configuration, and I'm experiencing a very strange issue. In gnome applications I can't do ` or ^ symbols. I press the keys, and nothing happens, no output. Strangely, I can do this symbols in KDE apps, so I guess this is not an X issue but gnome's.

Anyone has any idea on what could be wrong?

This is driving me nuts, since those symbols are used a lot in bash.

Experiment with different combinations in
```
gnome-keyboard-properties
```
I had to eliminate dead-keys to mine function properly.
Finnish layout in use.

---

### Post by danf_1979 on 2008-10-09
It worked thanks ;)

---

### Post by danf_1979 on 2008-10-09
Uhm, I can't do accent characters now, like áéíóú. I need dead keys, what should I do then? I guess this is a nasty bug.

---

