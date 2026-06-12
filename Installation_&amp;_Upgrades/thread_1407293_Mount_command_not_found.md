---
title: "Mount: command not found"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by AbdRahim on 2010-02-15
When I try to mount a network share after fresh install of Karmic on newly formatted partition, I get sudo: mount: command not found. I check the synaptic installer and it is in stalled. How do I get this working?

---

### Post by Cheezespread on 2010-02-15
Can you copy the entire command you were trying ?

And the result for this one too. ```
echo $PATH
```.

---

### Post by AbdRahim on 2010-02-17
Thanks for your response. It turned out not to be a Ubuntu problem after all. I was trying to mount an NAS share. Found solution and the mount commaqnd worked properly.

---

