---
title: "No Sound After update with Ubuntu 10.04"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by yourarunbabu on 2010-06-24
Hello guys,
I was using my  Ubuntu 10.04 without any issues and yesterday after an update the sound doesnt seem to be working!! Hope someone can help me out.

---

### Post by p0rnflake on 2010-06-24
Try checking the volume setting for the "Surround speakers" for some reason these beeing muted killed the sound to my "front" speakers.

---

### Post by yourarunbabu on 2010-06-24
I fixed it accidentaly :lolflag:
just reload alsa
<code>
sudo /sbin/alsa force-reload
<code>
:guitar:

---

