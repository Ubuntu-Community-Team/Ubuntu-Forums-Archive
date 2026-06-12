---
title: "no sound"
date: 2009-06-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ki4jgt on 2009-06-30
Ok, I just upgraded to koala last week, this week, I got some updates. After updating my system, my sound stopped working completely. Then I logged into root, and the sound, though laggish (paused before it started working) worked fine.

---

### Post by Regenweald on 2009-06-30
Try this.
```

sudo adduser 'your-username' audio

```

then go to /home./pulse and delete everything.

then reboot.

---

### Post by tjeremiah on 2009-06-30
> **Regenweald said:**
> Try this.
```

sudo adduser 'your-username' audio

```

then go to /home./pulse and delete everything.

then reboot.

just a little something. I tried that the other day, didnt have to deleted nothing and things worked. Just saying.

---

### Post by buzzmandt on 2009-06-30
had no sound and this fix worked.

didn't delete anything either, just restarted the comp and it worked

---

### Post by Regenweald on 2009-06-30
In my case i had to delete. Old config files files were causing a problem.

Edit: this fix worked right after i upgraded my system about 2 weeks ago and there's been a tonne of updates for pulse since then so yeah, not having to delete the contents of ./pulse if you just upgraded makes sense :)

---

### Post by ki4jgt on 2009-07-05
Sorry, but X-server went down after boyui (Hope I spelled that right), and I don't know very much command from just logging in and getting wifi working. had to install 9.04 again, don't want to upgrade again. killing internet connection, thanks for the help though.:guitar:

---

### Post by Regenweald on 2009-07-05
> **ki4jgt said:**
> Sorry, but X-server went down after boyui (Hope I spelled that right), and I don't know very much command from just logging in and getting wifi working. had to install 9.04 again, don't want to upgrade again. killing internet connection, thanks for the help though.:guitar:

No problem :) keep track of development, maybe you can join in at a later alpha stage.

---

