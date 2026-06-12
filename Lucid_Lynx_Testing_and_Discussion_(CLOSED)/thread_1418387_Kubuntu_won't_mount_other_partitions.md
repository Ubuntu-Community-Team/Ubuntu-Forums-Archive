---
title: "Kubuntu won't mount other partitions"
date: 2010-02-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by firstc624 on 2010-02-28
Ok i am trying to get kubuntu to mount my other partitions on my HD.  I have 1 windows partition, and 1 main ubuntu install.  My kubuntu install, alpha 3, is on a 3rd partition.  

Does anyone else have this problem or is this an isolated incedent?

How do i get this to work?

Thanks in advance...i didnt' want to file a bug report if this exists already.

---

### Post by cariboo on 2010-02-28
Do you get any errors when you try to manually mount the partitions.

---

### Post by firstc624 on 2010-02-28
Stupid me i forgot to put them in....here ya go.

"error occcured while accessing 243.7gib hard drive.  the system responded: org.freedesktip.hal.device.volume.permissiondenied: refusing to mount device /dev/sda5 for uid=1000"

Thanks

---

### Post by cariboo on 2010-02-28
It looks like a permissions issue, you should be prompted to enter a password  when mounting another drive or partition.

---

### Post by meborc on 2010-03-01
i think this has something to do with encryption...

i have similar issue when trying to mount a ubuntu partition, which is encrypted

will dig further ;)

---

### Post by timosha on 2010-03-01
The only way I can get other partitions mounted in Kubuntu is to use "sudo dolphin" in a terminal and then just click the partition. This is not the case in Ubuntu ! In Ubuntu a user can mount any partition.

---

### Post by firstc624 on 2010-03-01
> **meborc said:**
> i think this has something to do with encryption...

i have similar issue when trying to mount a ubuntu partition, which is encrypted

will dig further ;)

I know for me my drives are not encypted so i can't do anything w/ it.

If i run sudo dolphin i can acess them though.

---

### Post by Robertjm on 2010-03-01
You didn't mention it, but is this an NTFS drive? If so, did you install the NTFS-g and the NTFS Configuration Tool packages?

---

### Post by firstc624 on 2010-03-01
> **Robertjm said:**
> You didn't mention it, but is this an NTFS drive? If so, did you install the NTFS-g and the NTFS Configuration Tool packages?

no i am trying to access a ubuntu partition, ext4

---

### Post by envalin on 2010-03-24
I am having this same trouble, mounting an NTFS drive with KDE 4.4 with 10.04 Beta 1. Sudo Dolphin does work, however, but this gets annoying to have to do just to be able to load a collection from my "middle" shared partition of music into Amarok every time :P

---

