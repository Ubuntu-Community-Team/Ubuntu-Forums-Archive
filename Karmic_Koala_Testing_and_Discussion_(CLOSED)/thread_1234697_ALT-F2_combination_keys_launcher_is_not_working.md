---
title: "ALT-F2 combination keys launcher is not working"
date: 2009-08-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dentaku65 on 2009-08-08
I've noted that what ALT-F2 is not working on my box.
Anyone else have this issue?

---

### Post by phenest on 2009-08-08
Mine works. Is it setup in Keyboard Shortcuts?

---

### Post by dentaku65 on 2009-08-08
> **phenest said:**
> Mine works. Is it setup in Keyboard Shortcuts?

Yes, it is configured in Keyboard Shortcuts; does not work with compiz enabled and without compiz enabled too.

---

### Post by rudenko_ruslan on 2009-08-08
It works with Human theme, but doesn't with other themes (Dust, for example).

---

### Post by taavikko on 2009-08-08
> **rudenko_ruslan said:**
> It works with Human theme, but doesn't with other themes (Dust, for example).

works with all the themes I tried, theme shouldn't control the input-keys. (alt+F2)
So there might be a glitch on the config files.

---

### Post by dentaku65 on 2009-08-08
> **rudenko_ruslan said:**
> It works with Human theme, but doesn't with other themes (Dust, for example).

I'm using Humanity Theme. Switch back to Human does not work either, but I did not restart Gnome.

---

### Post by dentaku65 on 2009-08-08
> **taavikko said:**
> works with all the themes I tried, theme shouldn't control the input-keys. (alt+F2)
So there might be a glitch on the config files.

I'm afraid that you are correct.
Uneasy to find such config file I supposed...

---

### Post by Regel on 2009-08-08
I seem to be having the same problem. Alt+F2 is in the Keyboard Shortcuts, but it's not working. Using Human-theme, switching compiz on or off doesn't seem to affect it.

---

### Post by golusweet on 2009-08-08
> **Regel said:**
> I seem to be having the same problem. Alt+F2 is in the Keyboard Shortcuts, but it's not working. Using Human-theme, switching compiz on or off doesn't seem to affect it.

Same here.

It's not working.:confused:

---

### Post by nebosuke on 2009-08-08
This is probably this bug. [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/398826](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/398826)

---

### Post by taavikko on 2009-08-08
> **nebosuke said:**
> This is probably this bug. [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/398826](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/398826)

confirming this behaviour. just tested: solid color to panel and alt+f2 doesn't work.
switch back->killall gnome-panel and alt+f2 works again

---

### Post by phenest on 2009-08-08
> **taavikko said:**
> confirming this behaviour. just tested: solid color to panel and alt+f2 doesn't work.
switch back->killall gnome-panel and alt+f2 works again

Also confirmed. What a weird bug!

---

