---
title: "Noob asking again: Dual boot xp and ubuntu"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by Atro on 2007-11-26
OK guys, I know you had enough of noobs, but im really confused now.
I want to intall ubuntu on my computer and I dont want to loose my XP because I use programs like Flash and Photoshop
I got a 160G hard drive devided into 4 partions C,D,E,F each appx. 30G. All NTFS

Now what i read from topics in forums and google research was that i had to empty one of my partitions. F is empty now. I downloaded and burned Ubuntu live cd.

now the question is do I go one with installation and choose F as the partition Ubuntu uses or do i need to change the partition to something that linux can install on?

And in case anything goes wrong with ubuntu, will I be able to uninstall it without loosing my xp?

Thanks

---

### Post by MNICY on 2007-11-26
You want to make it so you have 3 partitions.
1. Your XP partition
2. Your Ubuntu partion
3. A Linux-Swap partition (very small size)

As long as you do NOT format your XP partition, then you will not loose any information.

gparted (or the partion editor on GUTSY) will help you edit partions easily.
DO NOT do a guided install in the installing process unless you know it i will not wipe you XP partion.
The really only safe thing i think is manual
But, if you dont know what your doing you could mess up.
So, read some guides on the internet (Google it :P) and when you are confident then do the dual boot.

To later remove Ubuntu, you should just be able to format the Ubuntu partion (and resize your XP to take up that space again) using the partition editor on the Ubuntu live CD :)

If you just want to use apps like photoshop, (not games becasue tey wont work with this properly) consider using a virtual machine inside Ubuntu with XP installed on it (like vmware or virtualbox). Saves alot of trouble dual booting if you just want to edit a picture or somthing.

---

### Post by pkands on 2007-11-26
I tried photoshop on a linux VM but couldn't print using photoshop's drivers with CUPS printers.

---

### Post by Pumalite on 2007-11-26
> **Atro said:**
> OK guys, I know you had enough of noobs, but im really confused now.
I want to intall ubuntu on my computer and I dont want to loose my XP because I use programs like Flash and Photoshop
I got a 160G hard drive devided into 4 partions C,D,E,F each appx. 30G. All NTFS

Now what i read from topics in forums and google research was that i had to empty one of my partitions. F is empty now. I downloaded and burned Ubuntu live cd.

now the question is do I go one with installation and choose F as the partition Ubuntu uses or do i need to change the partition to something that linux can install on?

And in case anything goes wrong with ubuntu, will I be able to uninstall it without loosing my xp?

Thanks

[http://video.google.com/videoplay?docid=-6104490811311898236](http://video.google.com/videoplay?docid=-6104490811311898236)

---

