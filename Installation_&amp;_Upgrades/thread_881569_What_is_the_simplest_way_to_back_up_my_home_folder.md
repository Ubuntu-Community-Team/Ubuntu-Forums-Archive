---
title: "What is the simplest way to back up my /home folder?"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by Sealbhach on 2008-08-06
I'm having difficulty understanding what is the best way to back up my /home folder.  

I read of one method which will only work if all the exact same folders are there, and another method which will only work if the partition size is identical to the previous one.

So, I just want to make a backup which can be restored under any circumstances, regardless of folders or partitions. Preferably a GUI.

Anyone know of anything like this?


.

---

### Post by iaculallad on 2008-08-06
That simplest way to backup your /home folder would be using the terminal:

```
cp -r  /home/your_username /media/sda1
```

---

### Post by Sealbhach on 2008-08-06
> **iaculallad said:**
> That simplest way to backup your /home folder would be using the terminal:

```
cp -r  /home/your_username /media/sda1
```

Thanks, what does that do? Does it make a copy of /home/username on the hard drive?

How about putting it on to a DVD? Copy to /media/????


.

---

### Post by iaculallad on 2008-08-06
> **Sealbhach said:**
> Thanks, what does that do? Does it make a copy of /home/username on the hard drive?

How about putting it on to a DVD? Copy to /media/????


.

That command will copy all the content of your /home/your_username directory to /media/sda1, as it uses the -r (-R) switch. Meaning, it copies recursively.

You could change the /media/sda1 to any mounted partition location you want as that is just an example terminal code.

---

### Post by NilsE on 2008-08-06
You could use the archive manager to create an archive which could then be updated periodically.  

Just go into Nautilus and right click the home folder and select archive.

You can then just store that archive anywhere you like.

---

### Post by akudewan on 2008-08-06
> **Sealbhach said:**
> 
How about putting it on to a DVD? Copy to /media/????


Under Applications > Sound and video, you can open Brasero. Create a data disc, and drag your entire /home/username folder.

---

### Post by Sealbhach on 2008-08-06
> **akudewan said:**
> Under Applications > Sound and video, you can open Brasero. Create a data disc, and drag your entire /home/username folder.


Now that's what I like!!!

Good one.


.

---

