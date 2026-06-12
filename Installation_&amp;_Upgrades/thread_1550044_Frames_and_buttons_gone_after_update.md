---
title: "Frames and buttons gone after update"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by dougalkerr on 2010-08-10
Why would the frames and buttons disappear after a regular update.

I rebooted which took back the buttons I was missing from the top=right corner of the windows but, the frames are still missing?

I am using a combination of Compiz and Metacity and until now all has been working really well.

I don't even have the awful window resize delay I was having.

Thanks...

---

### Post by ajgreeny on 2010-08-10
What do you mean by "frames and buttons"?

---

### Post by linux18 on 2010-08-10
```
 sudo apt-get purge metacity && sudo apt-get metacity && metacity --replace 
```
OR
```
 compiz --replace 
```

---

### Post by dougalkerr on 2010-08-10
Just solved the problem. I chose one of the Metacity themes and the frames around teh windows came back. Looks like Metacity settings had been reset to default and no theme selected.

Everything is working now.

---

