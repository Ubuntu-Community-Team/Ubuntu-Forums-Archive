---
title: "alsamixer turning down speakers and not remembering settings after reboot"
date: 2010-03-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by blakamin on 2010-03-06
Everytime I boot my laptop I have to run alsamixer to turn my speakers up to get any sound. Is there anyway I can make it permanently stay up?

---

### Post by cariboo on 2010-03-06
After you set the volume levels to where you want. run:

```
sudo alsactl store
```

to save the settings.

---

### Post by blakamin on 2010-03-06
Thank you but it didn't work

---

### Post by Dauthi4 on 2010-03-07
I solved that using the sound applet :

Sound applet > Sound preferences > Output

Try to change the setting at the bottom.

(Mine is now set to "Analog Speakers")

---

### Post by blakamin on 2010-03-08
Thanks... It'll do the trick, until I plug my headphones in and forget why they dont work;)

---

### Post by cyberkilla on 2010-03-08
> **blakamin said:**
> Thanks... It'll do the trick, until I plug my headphones in and forget why they dont work;)

I had to set mine to speakers too, and now headphone works, laptop speakers work and it isn't muted when you reboot.

---

