---
title: "after fresh 10.4 install no email sound notification"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by rebeltaz on 2010-06-17
I went to the mail-notification plugin and selected play sound and pointed it to a .wav file. When I click preview nothing is heard, nor does it play  when a new message come in. I can click on the same file in nautilus and it plays just fine. can someone help me figure out what I am doing wrong. Thanks...

---

### Post by lechien73 on 2010-06-17
You could try installing the Pulse Audio Volume Control:

```
sudo apt-get install pavucontrol
```

Then on the first tab (named Playback, IIRC), check to see that **System Sounds** aren't muted or turned down.

---

### Post by rebeltaz on 2010-06-18
I did and they are fine....

---

