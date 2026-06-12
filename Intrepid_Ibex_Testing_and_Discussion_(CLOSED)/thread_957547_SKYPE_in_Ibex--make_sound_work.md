---
title: "SKYPE in Ibex--make sound work"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by shuttleworthwannabe on 2008-10-24
I installed the Static version from the medibuntu repo's. (the normal version first, then decided to try the static vesion); speaker sound works (I can hear the "echo" call, but my voice is not recorded (i.e. microphone not capturing sound.

Intel HDA sound card, pulse audio system (hardware Acer travelmate 6292).

Anyone know how to fix this?

S

---

### Post by girishsasikumar on 2008-10-25
Yap SKYPE audio has issues with IBEX ............. though all other audio works fine

---

### Post by shuttleworthwannabe on 2008-10-26
any work around?

---

### Post by psyke83 on 2008-10-26
Look at my threads on PulseAudio.

In a nutshell: In Skype's sound options you need to ensure that Skype uses the "pulse" device for "Sound out" & "Ringing". You must set "Sound in" to your physical sound card's device.

Caveat: there seems to be a problem with ALSA's sound capture. You can try to workaround this issue by installing the OSS version of Skype, and launching it via the "padsp" wrapper.

---

### Post by shuttleworthwannabe on 2008-10-26
ok, thanx will give it a try.

---

