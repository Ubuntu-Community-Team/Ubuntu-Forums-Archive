---
title: "Pop sound when card initializes  Karmic"
date: 2009-05-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by lonniehenry on 2009-05-29
With the updates of 5/26 I get a popping sound when ever the sound card is initialized or shuts down.  I haven't had the problem before and my sound works okay.  I am using a NVidia sound card (HDA NVidia) Conexant analog. All sound preferences set to auto detect. I get this pop sound even when sound is muted.  What is the next step in stopping it from happening? I am using PA 0.9.15 
Thank you in advance.

---

### Post by psyke83 on 2009-05-29
> **lonniehenry said:**
> With the updates of 5/26 I get a popping sound when ever the sound card is initialized or shuts down.  I haven't had the problem before and my sound works okay.  I am using a NVidia sound card (HDA NVidia) Conexant analog. All sound preferences set to auto detect. I get this pop sound even when sound is muted.  What is the next step in stopping it from happening? I am using PA 0.9.15 
Thank you in advance.

That's because the HDA codec enables power saving by default, which is causing a pop each time the codec is powered back on.

Please open a bug according to these guidelines: [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-May/008239.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-May/008239.html)

---

### Post by lonniehenry on 2009-05-29
Thanks for the quick reply. I will file a bug.

---

### Post by taavikko on 2009-05-29
> **lonniehenry said:**
> Thanks for the quick reply. I will file a bug.

if I'm not mistaken You should file a new bug, not adding comment "me too" to an previously reported (by me)
Since there are multiple chipset affected.

Anyone can verify that this is the correct behaviour?

---

### Post by MacUntu on 2009-05-29
I'm not sure but I have reported a separate one. No way I manually add those 11 files. :D

---

### Post by lonniehenry on 2009-05-29
I think I reported it correctly this time.

---

### Post by psyke83 on 2009-05-29
> **taavikko said:**
> if I'm not mistaken You should file a new bug, not adding comment "me too" to an previously reported (by me)
Since there are multiple chipset affected.

Anyone can verify that this is the correct behaviour?

I'm pretty sure that they want separate bugs, yes. For each codec, they need to refer to the datasheet and find out if there is a method to nullify the codec pop.

The datasheet for my AC'97 codec documents a way to get rid of the popping, but I don't think Luke or Daniel have enabled powersaving for AC'97 codecs yet, just HDA for the moment.

---

### Post by gwydionwaters on 2009-10-13
how do i know which codec i am using to know if i need a new bug report?

---

