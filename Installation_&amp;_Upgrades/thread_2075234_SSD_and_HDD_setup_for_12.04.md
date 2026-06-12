---
title: "SSD and HDD setup for 12.04"
date: 2012-10-23
forum: Installation &amp; Upgrades
---

### Post by Djalmahal on 2012-10-23
Hi,

I want to install Ubuntu on my SSD (128GB) with the /home also on the SSD. On the HDD I will have another partition that will be used as a data storage for movies and other large files. 
How can I set it up that upon start up, Ubuntu doesn't even mount the HDD data partition, but will do so only after I open the folder "External Videos" on the HDD?
Does that makes sense. What about encryption on the HDD and should I use ext4?

Thanks for your advice.

---

### Post by Stoffel69 on 2012-10-23
Hope I understand you correctly with my reply.
Will "External Videos" be a folder on the HDD? If so you won't even be able to see this folder if HDD is not mounted.

I'll say encryption not necessary and ext4 should be fine.

---

### Post by Djalmahal on 2012-10-23
Yes, "External Videos" would be on the HDD.

---

### Post by Stoffel69 on 2012-10-23
Then i'll say no it won't be possable yo do it the way you want it to work.

---

### Post by oldfred on 2012-10-23
That is just what a default mount does. The default will be in /media as the label, or size.
But you need to label your partition on the rotating drive as External_Videos if you want a description. Then it mounts as the label.
 Not sure how many characters a label can be, so you may have to abbreviate?

Normally you want to mount automatically on reboot and give specify permissions & ownership rather than just the defaults. But then you have to edit fstab to mount partition.

---

### Post by pqwoerituytrueiwoq on 2012-10-23
using /etc/fstab ```
UUID=aa92d082-0e37-4e70-b696-7198daf30c62 /mnt/data           ext4    defaults        0       2
```i would do it like that and bind my folders to the desired location location like this

```
/home/me/Desktop /mnt/data/me/Desktop bind defaults,bind 0 0
/home/me/Documents /mnt/data/me/Documents bind defaults,bind 0 0
/home/me/Music /mnt/data/me/Music bind defaults,bind 0 0
```and so on and so forth

---

### Post by LiamOS on 2012-10-23
Install using the custom option, creating your desired partitions and so on. When you're finished installing, you could edit your /etc/fstab and add 'noauto' to the mount options for your desired partitions. You'd likely want to add 'user', too, so you can moutn them as a regular user.

I'd recommend xfs over ext4, particularly for a partition of movies and music. Encryption shouldn't be necessary, unless your movies and music include something you'd rather not have accessible to others, such as entire series of Barney, or Britney Spears.

---

### Post by Djalmahal on 2012-10-23
Great, thanks to everyone for their input. I'll look into fstab and it's uses.

---

