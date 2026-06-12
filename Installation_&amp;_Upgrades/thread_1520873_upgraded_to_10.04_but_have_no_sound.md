---
title: "upgraded to 10.04 but have no sound"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by whoya on 2010-06-30
Hello all, i updated to 10.04 about a week ago everything seemed to be working good. i downloaded alien arena and relised i dont have sound. upon further investigation i have found out the sound doesnt work on any program on ubuntu, so i got no sound on videos either. when i turn the volume right up all i hear is faint stactic. 
the sound works good in windows xp

thanks for your time

---

### Post by matt-fender on 2010-06-30
What motherboard if onboard sound? What sound card if not using on board?

Also try messing with the sliders in alsamixer

open a terminal and type

```
alsamixer
```

worth a try first :popcorn:

---

### Post by whoya on 2010-06-30
the motherboard is a Asus A8ne, i dont have a extra sound card. my sound used to work with jaunty. i think its a realtek ALC655. i tried moving the slides and options in alsamixer, still no sound :(

---

### Post by whoya on 2010-06-30
fixed it, the sound profile was set to input, i set it to output. movies and mp3 now have sound. 
thanks for your help matt-fender

---

### Post by matt-fender on 2010-06-30
Noice! Glad your sorted  mate! :guitar:

---

