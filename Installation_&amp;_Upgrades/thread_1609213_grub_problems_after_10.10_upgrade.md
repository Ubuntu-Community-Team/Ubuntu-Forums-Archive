---
title: "grub problems after 10.10 upgrade"
date: 2010-10-30
forum: Installation &amp; Upgrades
---

### Post by cowdogmoocat on 2010-10-30
I upgraded to 10.10, and grub just came back with "no wubildr", and then a "no other mode", or something like that:confused:. I dual boot xp (I used it to install wubi), and I need a few files off my linux partition. Is there a way to:
[LIST=1]
[*]recover my files within windows
[*]skip grub and go strait to ubuntu
[/LIST]

---

### Post by Rubi1200 on 2010-10-30
Can you still boot into Windows?

> skip grub and go strait to ubuntu

Not at this stage. First we need to know if you can access Windows and then we can move forward.

Just so you know; there is a problem with upgrading Wubi at the moment;
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Known%20Issues](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Known%20Issues)

---

### Post by bcbc on 2010-10-30
See this fix to get wubi booting [http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

To recover files from within windows use ext2read. It can give you readonly access if you point it at the \ubuntu\disks\root.disk file

---

### Post by cowdogmoocat on 2010-11-15
> **Rubi1200 said:**
> Can you still boot into Windows?


Not at this stage. First we need to know if you can access Windows and then we can move forward.

Just so you know; there is a problem with upgrading Wubi at the moment;
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Known%20Issues](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Known%20Issues)

yes, I can boot windows. in fact, I reinstalled ubuntu from there. I'm back at 10.04 now.

---

### Post by cowdogmoocat on 2010-11-15
I got my files back from the gmail server, and reinstalled wubi. I just need to know if 10.10 is safe.

---

### Post by Rubi1200 on 2010-11-15
If you did a fresh install and are able to boot into both Windows and Ubuntu, then the answer is yes, I suppose.

In any event, I am glad things worked out for you :)

Please mark this thread Solved using the Thread Tools near the top of the page if you think the problem has been resolved.

---

### Post by bcbc on 2010-11-15
> **cowdogmoocat said:**
> I got my files back from the gmail server, and reinstalled wubi. I just need to know if 10.10 is safe.

10.10 is probably as safe as any install. Just the upgrade to 10.10 doesn't work for wubi installs. The bug has not been addressed and it doesn't look like it is going to be anytime soon.

So, if you want 10.10 do a fresh install.

---

