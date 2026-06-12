---
title: "Nforce3 ultra + raid0 + Ubuntu 7.04... Possible?"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by Mr.Johnny on 2007-05-11
Hi! ):P 

Is raid0 possible on nforce based systems, running Ubuntu 7.04?

Thanks (Linux newbie).

---

### Post by honeydew on 2007-05-12
sure why not? Im running a raid 0.  you having trouble with something?

---

### Post by Mr.Johnny on 2007-05-12
Not yet... lol.
I was just wondering if it was possible.
You're using the sata_nv.c file available on nvidia's site, right? Or anything else needed?

Thanks ;)

---

### Post by honeydew on 2007-05-12
o no Im using software raid.. hrmm.. is the nvidia raid0 proprietary? sometimes it is some times it isnt.. if its in the bios.. then you should have no issues.. but I would recomend looking up the chipset on google.

---

### Post by psusi on 2007-05-14
You should read [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

---

### Post by Mr.Johnny on 2007-05-15
Nice... ;) Well, it seems that nforce3's bios nvraid is software based, but if I got this straight, with linux it does not matter if the bios supports raid or not, since the implementation is in the OS itself?

---

### Post by psusi on 2007-05-16
It matters in that in order to use the raid as configured by the bios, you have to configure your system differently, and it can be a PITA to get it working right.  The advantage is that you can boot directly from the raid.

---

### Post by Mr.Johnny on 2007-05-17
It was a PITA installing windows in a 4-disk array (an experience I don't intend to repeat so early) trying not to get any BSOD's during instalation... The bios-independent raid sound good to me... :D where do i start?

ps: sorry, didn't see the wiki link, i'll take a look

cheers.

---

