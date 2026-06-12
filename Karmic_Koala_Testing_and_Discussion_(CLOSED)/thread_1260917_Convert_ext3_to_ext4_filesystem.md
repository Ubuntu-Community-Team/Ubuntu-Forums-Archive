---
title: "Convert ext3 to ext4 filesystem"
date: 2009-09-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Funnnny on 2009-09-08
I've read the guide to convert ext3 filesystem to ext4 at [http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4](http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4)
But I read someone said that I'll not have all ext4 advantages if I use an converted ext4 partition.
So is it worth to convert my partition to ext4 now ? Or I should do a fresh install to have full advantages
Thanks

---

### Post by Kobalt on 2009-09-08
You'll effectively lose some of the performance converting ext3 to ext4. 
I'd recommend switching to ext4 when you reinstall your whole system.

---

### Post by forumache on 2009-09-08
I don't know how you use your system. For example, mine was not reinstalled since Ubuntu 6.04, just upgraded from release to release.

So, how did I upgrade from ext3 to ext4?

System partition:

I booted a Karmic Live CD
copied my system partition on a 4gb usb,
formated the disk to ext4
copied back the stuff from the stick,
modified the grub to use the new UUID
modified fstab to use the new UUID
rebooted => ext4, full performance

Home partition:
I booted a Karmic Live CD
converted from ext3 to ext 4
rebooted

now, of course this is not full performance for home, but...

copy a large directory from home somewhere, in a new place: it will be stored using new ext4 features
delete the old location
move the new directory where the old one used to be. => full ext4 performance on that directory

But of course, if you don't keep/care about data on your pc, you can just reinstall, it's the easiest, as Kobalt suggested

---

### Post by philinux on 2009-09-08
This is exactly what I've been pondering. I have home on it's own partition. Every new release I reinstall root and leave home unformatted. 

This approach has worked well since feisty fawn. Now we've got grub2 and ext4. So upgrading from jaunty to karmic is going to cause some anxiety I guess.

---

### Post by Funnnny on 2009-09-08
I've just upgrade Jaunty to Karmic. Everything is fine, at least :D
Converted my / to ext4, I think it's the best solution, I will have a fresh install when I have to reinstall Ubuntu.
Have some mess with nVidia and ext4, but after spend some times to reconfigure, everything is ok :D

---

