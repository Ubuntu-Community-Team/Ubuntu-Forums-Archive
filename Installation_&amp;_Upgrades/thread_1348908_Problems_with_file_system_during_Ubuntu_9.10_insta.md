---
title: "Problems with file system during Ubuntu 9.10 installation"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by Iskalla on 2009-12-07
I tried out Karmic Koala from live CD last night and was pretty blown away by how smoothly everything ran. I had no obscure errors or problems with drivers or codecs, and all my hardware worked fine, so I had high hopes for the installation and dual boot proccess. From what I have read, I understand I require a partition to boot from, a home partition and swap and root partitions. I created 70gb for home, 10gb for root, 500mb for boot and 4gb for swap using Windows Vista. I then went into installation and selected swap and ext3 file system during installation. The following screen bought up an error simply stating that it could not create an ext3 file system and simply took me back to the partition manager. Returning to Vista I had lost access to all these partitions, and was required to return to Ubuntu to format them back to ntfs, and this is where I am now. 

If it would help I can try and retrieve specfic error messages, although I am hoping it is just a straightforward mistake on my behalf and lack of understanding of how Linux works. My last experience was dual booting XP and Knoppix years ago, and whilst Knoppix itself had some problems the installation was fine.

As a last resort should I consider a clean Ubuntu installation, overwriting windows and then creating a partition for vista and reinstalling from Ubuntu?

Thankyou!

---

### Post by dhavalbbhatt on 2009-12-07
Take a look at the following guide, it will help you installing Ubuntu on your machine.

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

That being said, all you have to do is pop in the CD that you've burned and the partition manager will guide you (or you can do a manual partition as well) during the installation operation. You are also not required to have various partions for boot, home, etc., however, those are recommended. There is a lot of documentation on how to partition on [www.ubuntu.com](www.ubuntu.com), you should really read through all of that before installing Ubuntu.

Hope the above helps and welcome to Ubuntu!

---

### Post by Iskalla on 2009-12-07
Ok, I think I'm going to restore all my partitions to their original state and try installing Ubuntu from the disk whilst running Windows. That'd be Wubi right? And I'll have a read through some of the articles on those links!

---

### Post by darkod on 2009-12-07
> **Iskalla said:**
> Ok, I think I'm going to restore all my partitions to their original state and try installing Ubuntu from the disk whilst running Windows. That'd be Wubi right? And I'll have a read through some of the articles on those links!

Wubi is not the recommended way, but you can do that if you want. Just to let you know, you made mistake previously when creating partition for ubuntu from windows. Windows can't create partition for linux, it doesn't support linux filesystem. You should have left that space as blank, unallocated and the Ubuntu installer would do its job.
You can try again if you want to.

---

