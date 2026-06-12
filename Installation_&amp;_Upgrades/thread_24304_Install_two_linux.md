---
title: "Install two linux"
date: 2005-04-06
forum: Installation &amp; Upgrades
---

### Post by aradu on 2005-04-06
I want to install two Linux OSs on the same harddrive but the partitioner won't allow two '/' as label so I wonder how I would get around this.

And how would I do with the swap partition, do I need one or two of those?

---

### Post by lao_V on 2005-04-06
The way you do it is you install the first system normally (one /, one swap and rest free space) then you boot up from the other linux installation and install your 2nd linux on the free space

---

### Post by Equanimity on 2005-04-06
I would suggest also setting up a /boot partition at the front of the disk, and a /home partition, so you can share application settings, emails, etc between the two installations. The partition setup I'd recommend:

/boot
swap
/home
extended
 -> root1
 -> root2

---

### Post by Cool_dude_Prav on 2005-04-07
I would recommend using the same swap and using two different primary partitions for it...

If I am wrong someone plz correct me :wink:

---

### Post by risager on 2005-04-08
[QUOTE=Equanimity]I would suggest also setting up a /boot partition at the front of the disk, and a /home partition, so you can share application settings, emails, etc between the two installations. [/QUOTE]

I sort of agree. But sharing application settings, emails, etc between installation seem to require caution. You usally do not want two different versions of an application sharing the same data. This is asking for trouble.

---

