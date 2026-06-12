---
title: "[SOLVED] OS X say prog on Ubuntu?"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by romuald on 2007-07-09
Hello,
I'm totaly new to this community, and I want to thank it for his pleasantness. It helped me trough a lot of fixes.
Like in the subject already mentionned is it possible to use the "say" function from OS X under ubuntu?
Best regards,
Romuald

---

### Post by reclusivemonkey on 2007-07-11
> **romuald said:**
> Hello,
I'm totaly new to this community, and I want to thank it for his pleasantness. It helped me trough a lot of fixes.
Like in the subject already mentionned is it possible to use the "say" function from OS X under ubuntu?
Best regards,
Romuald

fesitval is a pretty good speech engine. Just 

```

sudo aptitude install festival

```

then

```

echo "hello" | festival --tts

```

---

### Post by romuald on 2007-07-12
thanks!

---

