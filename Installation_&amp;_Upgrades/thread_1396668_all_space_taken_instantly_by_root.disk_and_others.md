---
title: "all space taken instantly by root.disk and others"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by ItsAaron on 2010-02-02
Hi!

A few days ago I installed Ubuntu 9.10 with wubi, and every day I've had to delete various files in /var/log including 'kern.log', 'messages' and 'syslog' to ensure I have enough space to do my C programming. But they build up really fast, and that's not the problem now. 
Now my root.disk in /host/ubuntu/disks is 15GB and I'm fairly certain I shouldnt delete it.

I have no idea how to stop these logs building up or why the root.disk is so massive? If anyone could help that would be great.

Thanks in advance.

---

### Post by darkod on 2010-02-02
If you delete root.disk then you lose wubi. That is the root partition in wubi.
As for the size, I am not sure but maybe it is designed to take the whole space you dedicate to wubi. That doesn't mean it's full, you would only be able to check that from within wubi/ubuntu.
Something similar to virtual machines I've used earlier. The virtual hdd you create always takes the size you assign to it, but it has space inside. It's just how it works.
Wubi is similar to VM.

---

### Post by ItsAaron on 2010-02-02
Hi Darkod.

Thanks for the reply, but I dont think thats right, because its shown up as being smaller than that when i first installed wubi, and it has grown in size. When i ran the automatic disc checker that it prompts when i have low disc space that is what was taking it all up. I now cant save files or even compile a tiny C programme =[

---

### Post by darkod on 2010-02-02
I'm not using wubi and I might be wrong. I was only making a suggestion.
Also, as wubi is filling up with data, of course the root.disk file will grow even if it's small at the beginning.
I really don't know how was it designed to work. 15GB is really too much if we compare it with standard full ubuntu install which takes around 2.7GB default, and even with updates and adding software it doesn't grow too much.

---

### Post by ItsAaron on 2010-02-02
Yeah its wierd :/ 
But I've only got like 5MB of documents lol. Its just small C programmes =[
Ubuntu is gaying up on me

---

