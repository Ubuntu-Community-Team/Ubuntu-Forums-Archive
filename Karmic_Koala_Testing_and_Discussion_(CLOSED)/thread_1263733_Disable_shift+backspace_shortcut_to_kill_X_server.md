---
title: "Disable shift+backspace shortcut to kill X server"
date: 2009-09-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by henriquemaia on 2009-09-11
I don't know why, but since I've upgraded to Karmic, X assumes shift+backspace as shortcut to kill the server. How I disable this?

ps: I'm so tired of killing it by mistake...

---

### Post by henriquemaia on 2009-09-11
Solution - on a terminal, paste the following:

```
xmodmap -e "keycode  22 = BackSpace"
```

Voilá, no more accidental X server kills.

---

