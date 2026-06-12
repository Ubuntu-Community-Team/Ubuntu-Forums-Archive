---
title: "problem when trying to compile"
date: 2006-12-03
forum: Installation &amp; Upgrades
---

### Post by noneofthem on 2006-12-03
Hi there!

Since I updated to Edgy I have got a "slight" problem.

I cannot compile from source which is kind of a pain in the neck. I checked if the built-essentials are installed and everything seems to be fine. No idea where to look.

Do you have any idea what I might be missing?

Thanks for any help you may be able to provide..

Amir

---

### Post by Sef on 2006-12-03
What error messages do you get?

---

### Post by noneofthem on 2006-12-03
I am not sitting in front of my computer right now. I am at work (but don't tell anyone). I will post the message when I get home but it was something like a message saying that configure does not exist or something. Does that make any sense?

---

### Post by Sef on 2006-12-03
> will post the message when I get home but it was something like a message saying that configure does not exist or something. Does that make any sense?

yes, it makes sense.  Just copy and paste the error message from the terminal.

---

### Post by noneofthem on 2006-12-03
Here is the error message I get when I type "./configure":


bash: ./configure: No such file or directory


Hope anyone can help here...

Thanks

Amir

---

### Post by taurus on 2006-12-03
Are you sure you are in the right directory before you run that command, ./configure?  What's the output of this command then?

```
ls -la
```

---

