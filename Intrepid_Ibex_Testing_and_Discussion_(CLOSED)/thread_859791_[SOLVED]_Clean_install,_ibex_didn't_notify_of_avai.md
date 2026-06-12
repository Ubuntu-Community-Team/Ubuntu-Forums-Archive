---
title: "[SOLVED] Clean install, ibex didn't notify of available restricted driver"
date: 2008-07-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mattismyname on 2008-07-14
Back with Hardy, if I did a fresh install it would pop up a message in the notification area saying there was a restricted driver available for my nvidia video card.  With Ibex no such popup appeared.

Playing the newbie, I searched for nvidia in synaptic and got about 100 results.  

What's up?

---

### Post by autocrosser on 2008-07-14
Right now the whole driver issue is being worked on--Jockey-gtk is not working with the new packaging of Nvidia drivers. Just install nvidia-177 (for 6xxx & newer)-- You "should" also install--nvidia-173-modaliases, nvidia-177-kernel-source, nvidia-177-modaliases, nvidia-71-modaliases, nvidia-96-modaliases, nvidia-common, nvidia-glx-177 & nvidia-settings.

Then wait for Jockey to be fixed.....

---

