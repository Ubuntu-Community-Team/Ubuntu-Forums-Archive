---
title: "Unable to create custom iso for Ubuntu"
date: 2022-01-29
forum: Installation &amp; Upgrades
---

### Post by abcf on 2022-01-29
Nice to meet you.
I was wondering whether to post, but I will post it.


I started to modify Ubuntu the other day and am trying to make an iso image of it, but I'm having trouble with the old method that doesn't work now.
Does anyone know how to make a custom iso for Ubuntu today?

---

### Post by tea for one on 2022-01-29
This may help you.

[https://launchpad.net/cubic](https://launchpad.net/cubic)

---

### Post by oldfred on 2022-01-29
Do you need a custom ISO?
If installing same configuration many times, it may make sense.

But if wanting to just be able to do a new install, you can backup system, which you should do anyway and then restore from backup.
Your backup does not have to include system as you can easily reinstall Ubuntu.
Backup should include /home which has all your user settings. a list of installed apps to make it easy to reinstall, any other data partitions or server type apps that may be in / (root). If you changed any system wide settings, you may want those from /etc. I used to just copy the few files I edited into /home. But now have a script that automatically edits those files.

---

### Post by abcf on 2022-01-30
Thank you for your answer.
I used Cubic as a practice to make an original Linux OS, but I don't know how to use it, and the original Ubuntu iso comes out, so I'm looking for other means as well.

---

### Post by abcf on 2022-01-30
make an original Linux OS&#8594; make an custom Linux OS

---

### Post by tea for one on 2022-01-30
> **abcf said:**
> I used Cubic as a practice to make an original Linux OS
Therefore, you have already created an Ubuntu Custom ISO?
> **abcf said:**
> but I don't know how to use it  
You use it as you would use a regular Ubuntu ISO. Boot into a live session, explore the system and then install it if you wish.
> **abcf said:**
> and the original Ubuntu iso comes out,
I do not know what you mean?

There are many guides/instructions available on the internet and a bit more research may be required.
Also, the Cubic developers are very responsive to questions [https://answers.launchpad.net/cubic](https://answers.launchpad.net/cubic).

---

### Post by abcf on 2022-01-31
Thank you. I ask them.

---

