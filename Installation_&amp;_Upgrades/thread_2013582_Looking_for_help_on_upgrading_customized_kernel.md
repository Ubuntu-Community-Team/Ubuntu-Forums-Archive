---
title: "Looking for help on upgrading customized kernel"
date: 2012-07-01
forum: Installation &amp; Upgrades
---

### Post by ldxstc on 2012-07-01
Hi

I am using ubuntu 11.10 with kernel 3.4.4. I upgraded from 3.0.0 by using dkpg. It was sucessful.However when I try to build 3.4.4 kernel by using the default config and boot with it, it complains that it can not find the root drive.

I think I might not set up the build configuration correctly for ubuntu. Can anyone give me some suggestions?

Thanks

Will

---

### Post by DJ_Max on 2012-07-01
What's the reason you have for using 3.4.4 kernel?

---

### Post by ldxstc on 2012-07-01
> **DJ_Max said:**
> What's the reason you have for using 3.4.4 kernel?

Thanks for reply. I am learning kernel, so sometime I need to do some modification on kernel code to test my thought. But I am a newbie and could not find a right OS to play with. Now days the Linux OS are so diff from what they describe in book:(. Can you give me some suggestions?

Thanks

Will

---

### Post by DJ_Max on 2012-07-01
To be honest, I wouldn't use Ubuntu to test kernel configs. I would use something like Gentoo

---

### Post by ldxstc on 2012-07-01
hmm...can you explain y ubuntu is not good in this case? thanks

---

### Post by DJ_Max on 2012-07-01
Ubuntu has been crafted to be a mainstream desktop. Customizing something as low-level as a kernel essentially degrades the integrity of Ubuntu. They have kernel specific for it's OS, when you try to break out of the normal software you will run into weird problems in my experience.

---

### Post by ldxstc on 2012-07-01
Hmm make sense... Thanks a lot. I will go fro gentoo~~

---

