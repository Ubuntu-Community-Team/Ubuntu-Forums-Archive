---
title: "Update yesterday"
date: 2010-02-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Jackzor on 2010-02-26
Borked my system. I see a flash of words and it says something about errors in the file system.

I can't boot into anything. Any ideas on what I should do? I DO NOT want to format :P Unless I can back up all my config files. For themes and such.

---

### Post by mikeyphi on 2010-02-26
How about booting into a Live-CD?

---

### Post by Jackzor on 2010-02-26
I'm sure I will be able to do that. I'm just waiting till I get my hands on a blank cd. What will I need to do after I boot to it?

---

### Post by philinux on 2010-02-26
> **Jackzor said:**
> Borked my system. I see a flash of words and it says something about errors in the file system.

I can't boot into anything. Any ideas on what I should do? I DO NOT want to format :P Unless I can back up all my config files. For themes and such.

Does it drop you into a command line?

If so then run fsck manually.

```
fsck -v /dev/sda**[COLOR="Red"]X[/COLOR]**
```

Where X is you root partition. It may offer to fix things.

---

### Post by Jackzor on 2010-02-26
Well.. There was no command line just the blinking cursor.

But, all is well.. It seems to have fixed itself.

---

