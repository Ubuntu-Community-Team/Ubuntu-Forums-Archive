---
title: "does anyone have a dell m1330 with working suspend?"
date: 2009-08-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nanog on 2009-08-09
suspend has been broken for me since rc4 and the pm-trace script does not give me squat (i've blacklisted every driver that generated a hash match). 

does anyone else have an m1330 and, if so, is their s2ram working?

(suspend works perfectly with 2.6.28-30)

---

### Post by rednus on 2009-08-10
> **nanog said:**
> suspend has been broken for me since rc4 and the pm-trace script does not give me squat (i've blacklisted every driver that generated a hash match). 

does anyone else have an m1330 and, if so, is their s2ram working?

(suspend works perfectly with 2.6.28-30)

I do.. and it works perfectly for me.. with standard 2.6.31-5 generic kernel and also my custom kernel based on the generic version..

---

### Post by nanog on 2009-08-10
rednus,
are you using the 64 bit kernel?

---

### Post by nwadams on 2009-08-11
i haven't had any problems with suspend, nor hibernate...well other than the one where i was getting booted back to gdm when compiz was enabled

---

### Post by rednus on 2009-08-11
> **nanog said:**
> rednus,
are you using the 64 bit kernel?

Yes I am.

---

### Post by rednus on 2009-08-11
> **nwadams said:**
> i haven't had any problems with suspend, nor hibernate...well other than the one where i was getting booted back to gdm when compiz was enabled

Used to have reboot to gdm problem earlier.. but now nada.. disappeared into thin air.. everything works a treat.. even webcam.. which i didnt expected to :)

---

### Post by nanog on 2009-08-12
thanks for the reply, rednus. now i have to figure out what i did to bork suspend.

---

