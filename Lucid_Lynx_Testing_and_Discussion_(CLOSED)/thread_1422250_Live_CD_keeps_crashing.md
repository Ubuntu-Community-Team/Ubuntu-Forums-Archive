---
title: "Live CD keeps crashing"
date: 2010-03-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by pedrom169 on 2010-03-05
Not sure if its the correct place.

I have downloaded the 10.04 iso and burnt it to disc at low speed.
When i load it up on my laptop it is okay for around 1-2 minutes then crashes with a funky coloured square at the top left hand corner.

Any know had this error?

Thanks

---

### Post by ibuclaw on 2010-03-05
What type of Graphics Card do you have?

---

### Post by pedrom169 on 2010-03-05
On the manufactures webpage it has a ati radeon/firegl.

---

### Post by pedrom169 on 2010-03-07
anyone have a idea?

---

### Post by pedrom169 on 2010-03-08
I have even tried the daily cd. Nothing seems to work

---

### Post by pedrom169 on 2010-03-12
Does anyone know? Or should i just wait for beta 1?

Thanks

---

### Post by VMC on 2010-03-12
Just to let you know your not alone. I read your problem, and it may be related to Plymouth. I don't have an ATI video. 

A couple of things to try. Check you home folder ".xsession-errors" & ".xsession-errors.old". See if anything there helps.

Also try looking a "/var/log".

One thing you can try is to remove plymouth and see if that helps. Also try using "nomodeset" at the end of your "linux" line.

---

