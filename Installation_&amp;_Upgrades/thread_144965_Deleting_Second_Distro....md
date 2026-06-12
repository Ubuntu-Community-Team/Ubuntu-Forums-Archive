---
title: "Deleting Second Distro..."
date: 2006-03-15
forum: Installation &amp; Upgrades
---

### Post by LongTooth on 2006-03-15
Don't know for certain where to put this so if the moderators wish to move it, please do.

This is my second go-round with dual booting. I didn't like it the first time and I don't like it now. Why, oh why did I do it? That question is a topic for another time. Luckily all this has taken place on a second machine. Breezy is still working like a champ on my main PC. 

Anyway, the first time I ended up reinstalling my distro of choice. This second time, since I've put a lot of work in, I'd like to save it. Here's what I've got: Debian/Testing and Dapper Drake on one drive. I'm done playing with Dapper (I think I'll wait for the final release) and would like to reclaim the disk space I've used for Dapper Drake. But I don't know how to go about it. It was easy enough to install the second distro but I'm afraid it's going to be a bear to clean this up. At least it seems so to me. 

I know I'll have to alter the MBR so Etch will boot up and some how delete the Ubuntu/Drake listing. My 40Gb HD is split evenly between the two. 20Gb for Debian/Etch and 20 for Ubuntu/Drake. So where do I start first?

I've done some Googling and forum searching but the only thing I can come up with is how to dual install OSs and not how to clean up my mess. 

Any and all assistances will be greatly appreciated.

Thanks,

---

### Post by mstlyevil on 2006-03-15
I will move it to the appropiate forum for you. ;)

---

### Post by SSTwinrova on 2006-03-15
Never tried this before, but the following would be along the lines of what I'd attempt:

1. Remove all partitions being used *only* by Ubuntu (i.e. not a shared swap, boot, etc.)
2. Expand (if you want) your Debian partition
3. Delete the Ubuntu entries in menu.lst

---

