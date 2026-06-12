---
title: "Audigy 2 No Sound By Default"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-10-05
Ive been doing a workaround with this bug:

[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/106380](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/106380)

Where I run alsamixer in a terminal and toggle the digital out to off.

Now when I run alsamixer after doing a fresh install from the current live cd, I get a pulse audio card and chip. I need to get into the actualy audigy sound card like I used to be able to do in alsamixer to toggle digital out.

How do I do this now? thanks

---

### Post by mc4man on 2008-10-05
Did you try double left clicking the speaker icon in upper panel?

---

### Post by plun on 2008-10-05
I have also a Audigy 2 card and my latest install is from Alpha 6

```
alsamixer -Dhw
```

Gives you the hardware mixer

I am going to wait a week and perform a clean install, too many errors
within the beta... (also have a server running with beta)

---

### Post by Nullack on 2008-10-05
Your the man Plun :) Thats exactly the command I needed

---

