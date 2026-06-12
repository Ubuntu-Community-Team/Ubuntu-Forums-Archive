---
title: "Random uvesafb problems on boot"
date: 2008-08-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by roger99 on 2008-08-21
Hi,

Is anybody else getting seemingly random problems with uvesafb immediatly after the kernel becomes 'alive'.  When Usplash usually appears on screen I get loud beeping from the speaker, guaranteed, with sometimes a blank screen, sometimes text, something along the lines of 
[B]
uvesafb: failed to execute v86d.[/B]

Sometimes, the beeping stops and it carries on booting sometime not,  sometimes it simply boots problem free.

I've installed v86d but it still happens, although I have done no post install config on v86d so maybe this still needs to be done?.

I've tried looking through the logs in /var/log but can find no mention of the error (am I looking in the right logs?)  

Is this a bug I should be reporting on launchpad or is it something upstream?  Such as kernel development.

Any thoughts anybody?

UPDATE: I've done some searching on Launchpad and this seems to be a well known bug, sorry, should have researched first.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246269](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246269)

---

