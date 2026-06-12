---
title: "New partition can't create folders; space used up immediately."
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by jcd29 on 2010-08-29
Just created a new ext4 partition in my 320GB hard drive. It was a 248GB partition, but when I right click from the main menu and dlick Properties, I get that 12.6GB have already been used AND that the total capacity is 244 GB. What's up there?

I also can't create new folders or files in it.

---

### Post by jcd29 on 2010-08-29
I'm guessing I have to modify the permissions? I thought just partitioning from my user would do the trick.

---

### Post by jcd29 on 2010-08-29
Should I give it 777 permissions? It's on /media/devicelabel

I'm thinking about just using chown to change ownership to my username, since I dunno if it being owned by root is really necessary.

---

### Post by jcd29 on 2010-08-30
Any help would be greatly appreciated.

---

### Post by oldos2er on 2010-08-30
To change ownership to yourself, run **sudo chown -R user:user /media/devicelabel** where "user" is your username. You should now be able to create files/folders on it.

ext3/ext4 reserves 5% disk space; this can be changed with **tune2fs** if you wish.

---

### Post by jcd29 on 2010-08-30
> **oldos2er said:**
> To change ownership to yourself, run **sudo chown -R user:user /media/devicelabel** where "user" is your username. You should now be able to create files/folders on it.

ext3/ext4 reserves 5% disk space; this can be changed with **tune2fs** if you wish.

Thanks a lot for your answer.

Oh yeah, I was just wondering if I *should* change ownership of it.

Would it do any good to reduce that 5%, or is it better just to leave it alone? 

Also, I do get that 5% of the 244GB would be around 12GB (which is the amount that's in use right now), but why is it 244GB in the first place, when the partition was supposed to be 248GB?

---

### Post by oldos2er on 2010-08-30
> **jcd29 said:**
> Oh yeah, I was just wondering if I *should* change ownership of it.

Would it do any good to reduce that 5%, or is it better just to leave it alone?

Those are questions you'll need to answer for yourself, depending on how you wish to use your system. If it was me, I'd leave the 5%, and take ownership.

Not sure about the 4GB discrepancy.

---

### Post by jcd29 on 2010-08-30
> **oldos2er said:**
> Those are questions you'll need to answer for yourself, depending on how you wish to use your system. If it was me, I'd leave the 5%, and take ownership.

Not sure about the 4GB discrepancy.
Thanks. One last thing: Should I change ownership/permissions only in the mount point, or in the disk itself (sdb1) too?

And I'm trying to make the mount point /media/Data Ubuntu, but it doesn't work. I can create the path with sudo mkdir Data\ Ubuntu, but when editing fstab it says there's an error. I used "dataubuntu" instead, and it worked. But I wanna know if there's a way to use spaces.

---

### Post by jcd29 on 2010-08-31
Done.

I used **sudo chown -R user:user /media/devicelabel** to change ownership, and **sudo chmod -R 750 /media/devicelabel** to change permissions.

I still wish I could've named it Data Ubuntu instead of dataubuntu, but I couldn't solve that fstab problem. Any ideas?

---

### Post by oldos2er on 2010-08-31
> **jcd29 said:**
>  But I wanna know if there's a way to use spaces.

Not that I'm aware of. You could use Data_Ubuntu or Data.Ubuntu

---

### Post by jcd29 on 2010-08-31
> **oldos2er said:**
> Not that I'm aware of. You could use Data_Ubuntu or Data.Ubuntu

Ah, well. My Data XP gets mounted easily, but that one's not in fstab (nor do I want it there), so I guess that's the problem, you can't have spaces in fstab. Thanks.

---

