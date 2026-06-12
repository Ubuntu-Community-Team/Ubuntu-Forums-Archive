---
title: "I can’t boot after update 19.04"
date: 2019-04-20
forum: Installation &amp; Upgrades
---

### Post by serhatseval on 2019-04-20
Hello, today i upgraded to 19.04. But after installation i couldn’t boot because there was only black screen. I tried nomodeset then i got hdaudio hdaudioC0D2: Unable to bind the codec error. I can’t boot still. Thanks.

---

### Post by VMC on 2019-04-20
If you get grub menu screen, type "c", then find "linux" line, and remove quiet, splash at the end, then push "F10" key. See if any messages come up.

---

