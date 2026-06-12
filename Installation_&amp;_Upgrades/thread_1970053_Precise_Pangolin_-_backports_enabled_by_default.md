---
title: "Precise Pangolin - backports enabled by default?"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by djgrant on 2012-04-30
So after upgrading from Feisty all the way up to Oneiric, I finally decided to to a clean install of Precise Pangolin. It looks like the backport repository is enabled by default, but I don't remember this being the case in older releases. Is it pretty safe/stable to enable the backports repository?

---

### Post by Frogs Hair on 2012-04-30
Proposed updates and backports shouldn't be activated by default . I use proposed updates but, beware of partial upgrades if you enable either .

---

### Post by djgrant on 2012-04-30
> **Frogs Hair said:**
> Proposed updates and backports shouldn't be activated by default. I use proposed updates but, beware of partial upgrades if you enable either .

Well backports were enabled by default. At least I'm pretty sure they were. It caught my eye immediately when I opened the software sources dialog because I'm so used to seeing that checkbox un-checked.

What do you mean by beware of "partial upgrades"? Why should one beware? And what is a partial upgrade?

---

### Post by wojox on 2012-04-30
It's default since last release. [COLOR="Red"][source]("https://help.ubuntu.com/community/UbuntuBackports#Using_Backports")[/COLOR]
> On releases after and including Ubuntu 11.10 (Oneiric Ocelot), this is not necessary, as apt is configured with Backports enabled by default. 

---

### Post by subhadip_sky on 2012-05-01
> **wojox said:**
> It's default since last release. [COLOR=Red][source]("https://help.ubuntu.com/community/UbuntuBackports#Using_Backports")[/COLOR]

Thanks for the info. I also got confused as I remember in the previous releases, it would come unchecked by default. Somebody should mark this thread as SOLVED.

---

