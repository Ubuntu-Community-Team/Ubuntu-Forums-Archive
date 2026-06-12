---
title: "mounting point and file system"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by Peter_Bingo on 2008-11-22
Just go my free CD today and was too excited to come here and ask a few questions. I have run the install but as soon as i get to the partition editor it's now asking me where to the mounting point and which file system to go with. i am running ubuntu 8.04 on a laptop which I think is using a fat 32 file system. Should i do the same here? or format to something different? And which mount point should I use.

Thanks in advance!:)

---

### Post by taurus on 2008-11-22
Is there any other OS on that laptop?  If you want to install Ubuntu on that drive as your only OS, then tell the installer to use the whole disk and it knows what to do next.  But if you already have another OS on it and just want to install Ubuntu along side it, then you tell the installer how much space you want to give to Ubuntu.  And the filesystem for Ubuntu, default, is ext3.

---

### Post by Peter_Bingo on 2008-11-22
> **taurus said:**
> Is there any other OS on that laptop?  If you want to install Ubuntu on that drive as your only OS, then tell the installer to use the whole disk and it knows what to do next.  But if you already have another OS on it and just want to install Ubuntu along side it, then you tell the installer how much space you want to give to Ubuntu.  And the filesystem for Ubuntu, default, is ext3.

I have windows xp and vista on my computer and i also wanted ubuntu on it. I have already told the installer how much i want on it. I will use the ext3 system like you said but what should i use as the mounting point then?

---

### Post by Idefix82 on 2008-11-22
How much space do you want to allocate to Ubuntu? The one mount point that you definitely need is / and it should be formatted as Ext3. You might also want to create a SWAP partition (otherwise you won't be able to hibernate the laptop and also SWAP can be used as additional RAM) and possibly a /home partition, also formatted as Ext3. The latter will contain your user preferences and data, like documents, music,...

---

### Post by Peter_Bingo on 2008-11-22
> **taurus said:**
> Is there any other OS on that laptop?  If you want to install Ubuntu on that drive as your only OS, then tell the installer to use the whole disk and it knows what to do next.  But if you already have another OS on it and just want to install Ubuntu along side it, then you tell the installer how much space you want to give to Ubuntu.  And the filesystem for Ubuntu, default, is ext3.

I have windows xp and vista on my computer and i also wanted ubuntu on it. I have already told the installer how much i want on it. I will use the ext3 system like you said but what should i use as the mounting point then? And btw the laptop is a totally different computer

---

### Post by Peter_Bingo on 2008-11-23
Finished up and running! Thanks!:)

---

