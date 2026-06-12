---
title: "LiveCD not working in UEFI, but works in Legacy"
date: 2013-10-19
forum: Installation &amp; Upgrades
---

### Post by wyEJWE8 on 2013-10-19
On my HP Elitebook 8570W I want to install ubuntu besides the pre-installed windows 8. THe problem is that booting from legacy mode works properly and i will get the live version of ubuntu. Unfortinuately thats not the case when i try to boot the same dvd from UEFI mode. In that case i will get something like "cannot read sector 0x69c00 on cd0". Does anyone know what might be causing this problem, and how to prevent this from happening, since i would like to use UEFI on my laptop.

(Im sorry, but my english is not as good as i wished it would be)

---

### Post by sanderj on 2013-10-20
Did you read this: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) ?

---

### Post by wyEJWE8 on 2013-10-20
Yes, i did read it for sure, (its the way i ended up here). But I have tried disabling Fastbood, secureboot and i cant find intel smart something, eventhough i have a msata slot in my pc. On the other hand, i am afraid i will mess up my pc if im gonna make too much changes to it, because i will need it. All the problems i can find on the internet are windows booting problems after installation, but nothing if something goes wrong with my ubuntu disk.

---

### Post by fantab on 2013-10-20
Are you certain that you have UEFI boot with Windwos8? 

Boot from Ubuntu DVD 'legacy' and open Terminal [Ctrl+Alt+T] and post the output you get from the following command:

```
sudo parted -l
```

---

