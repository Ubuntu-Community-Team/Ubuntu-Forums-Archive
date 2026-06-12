---
title: "what drive size would you recommend?"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by ayet on 2007-10-30
when you partition your drive for ubuntu installtion you specifiy the root drive and the swap drive.
just want to know what is the recommended size in GB for a swap drive space. I have 1GB of ram installed on my system. and just 10gb for my linux. and just use it for internet and playing movies.

---

### Post by Crafty Kisses on 2007-10-30
> **ayet said:**
> when you partition your drive for ubuntu installtion you specifiy the root drive and the swap drive.
just want to know what is the recommended size in GB for a swap drive space. I have 1GB of ram installed on my system. and just 10gb for my linux. and just use it for internet and playing movies.

I'd suggest atleast 15GB.

---

### Post by markusf21 on 2007-10-30
you don't need 15 gigs for /swap 2 or 3 is plenty

---

### Post by Crafty Kisses on 2007-10-30
> **markusf21 said:**
> you don't need 15 gigs for /swap 2 or 3 is plenty

Oh, I thought he meant for the whole installation, my bad.

---

### Post by wieman01 on 2007-10-30
_My recommendation:_

SWAP -> 1 GB (= 1 GB of RAM)
ROOT -> 6 GB
HOME -> 3 GB

That would probably do. Pretty much what I have.

---

### Post by wieman01 on 2007-10-30
By the way... you really ought to have HOME and ROOT on a separate partition. Imagine the ROOT file system gets corrupted, you'd lose all your precious personal data as well. My ROOT drive crashed once (silly mistake on my part) and what saved me was the fact the HOME was on another partition.

---

### Post by ijkn on 2007-10-30
> **wieman01 said:**
> _My recommendation:_

SWAP -> 2 GB (= 2 x 1 GB of RAM)
ROOT -> 5 GB
HOME -> 3 GB

That would probably do. Pretty much what I have.


wow....2GB use it for swap........is it too much?
I think 0.5GB or 1GB is far from enough.

---

### Post by wieman01 on 2007-10-30
> **ijkn said:**
> wow....2GB use it for swap........is it too much?
I think 0.5GB or 1GB is far from enough.
Oh man, you're right... typo. Should be 1 GB infact. Thanks, man.

---

### Post by FredB on 2007-10-30
Swap : 1 or 2 gb
Root : 2 or 3 Gb
Home space : rest of it.

---

### Post by wieman01 on 2007-10-30
> **FredB said:**
> Swap : 1 or 2 gb
Root : 2 or 3 Gb
Home space : rest of it.
2 - 3 GB for root is not enough in my experience. Actually my 6 GB are almost fully utilized... Although I have removed all DEB archives and temporary files.

---

### Post by rml695 on 2007-10-30
Since this is about installations, relating to drive size, I was wondering if anyone could help me. Okay, I have a Sony Vaio UX280P Micro PC running Windows XP Pro. The drive's capacity is 30 GB, and XP seems to be using 10 of them. I'd like to set up a dual boot partition, and according to my calcuations; for a 50/50 split I'd have 15 GB free (with Ubuntu and XP both on the system), thus translating into 7.5 GB per system. My uses for the system are mostly internet, but also taking photos or vidoes (occasionally), and also taking notes in class (via Microsoft Works, and Open Office once I get Ubuntu installed). Would 7.5 GB of free space still enable a stable system (particularly on the Windows side, as I'm going to be a future Teacher of the Visually Impaired and would need to keep up with the technology, and most businesses where an individual with low vision would work would be using Windows)? I'm fed up with Windows, and would like to be rid of it forever, but as I just stated I can't abandon it. Should I get an external hard drive and use that for storage or should I just keep my notes (which are currently on the system) there, and chance it? You can e-mail me if you wish. I'm a brand new member so I'm not sure if thread posts relating to this would end up in my email as a notification or not. Thanks in advance for your help, guys. :)

---

### Post by kennedyjch on 2007-10-30
I have 7.10 installed with 9GB for Linux; 1 GB for swap (I have 2 GB ram); on top of that I have 5 GB /home partition.

9GB is a little lean if /home is there, for if you install applications like Google Earth and CrossOver (consumes lots of space for Window$ application installs), you may hit the wall quickly.

---

