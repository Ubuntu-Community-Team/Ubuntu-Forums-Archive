---
title: "What does the installation size mean?"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by ahriman22 on 2008-06-25
So i'm, re-installing Ubuntu and vista for different reasons. I'm using the installer in vista to install it and the ubuntu installation is asking me "Installation size". I don't know what it means, does it mean how big ubuntu itself is going to? Or does it mean the assigned number, like...8 would be the max GB of the hard drive used in total by the OS and applications and files?

---

### Post by earthmeLon on 2008-06-25
If you are having Ubuntu automatically set up your partitions, I'm **pretty** sure that it's asking you how much space you want the TOTAL Ubuntu partition, which is where it would be installed.  Thus, if you chose 8GB, on a 250GB HDD, Ubuntu will leave Windows with 242GB, and steal 8 for itself :D

---

### Post by avtolle on 2008-06-25
I infer you are using Wubi to install Ubuntu within Vista. If so, the question is asking you how large you want the "virtual disk" created for Ubuntu to be.

---

### Post by ahriman22 on 2008-06-25
Virtual disk on my partition? Yes i'm using Wubi and i made a partition of 26GB, since i quickly ran out of the 10GB i had previously made. So if i choose 8GB, than i'll only be able to use 8GB of my 26GB partition?

---

### Post by avtolle on 2008-06-25
Yes, you would only be able to use 8GB.

EDIT: You understand that Wubi will be installed as a folder under Vista, much like other programs are, and as such, will reside on the Vista Partition. Now, I'm aware of threads on the Wubi Forum discussing installing to another hard drive, but again, the hard drive partitions are under Windows, be it Vista, XP or whatever. So, if you created a specific 26 GB partition for Ubuntu, unless you install under Vista directly to that partition, you're going to be space limited by the room available on the main Vista partition. Hope I didn't confuse you more, here.

---

### Post by ahriman22 on 2008-06-25
No, you did not confuse me. Thanks.

---

