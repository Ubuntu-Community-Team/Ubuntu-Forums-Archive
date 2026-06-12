---
title: "Hard Disk Mounting Issues"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by ubun7upanz3r1337 on 2007-06-19
During installation of Ubuntu 7.04 i encounter an error where it says that it cannot unmount the Hard Disk (Windows) partition. I have 10 GB space for Ubuntu 1GB swap space and i am running a dual core Toshiba M110. Can anyone help?

Specs
Toshiba M110
Intel Core Duo @ 1.73 GHz
Intel GMA 950
60 GB HDD

---

### Post by merlinus on 2007-06-19
Are you installing from the live cd, or some other method?

-merlin

---

### Post by ubun7upanz3r1337 on 2007-06-19
Live CD, i have used GParted to make 10GB of free space.

---

### Post by Pumalite on 2007-06-19
> **ubun7upanz3r1337 said:**
> Live CD, i have used GParted to make 10GB of free space.

If Windows is Vista, you have to partition FROM Vista.

---

### Post by merlinus on 2007-06-19
Try this from a terminal:

```

sudo fdisk -l

```

(l is a lowercase L)

This will show your partitions.

Assuming windows is dev/hda1:

```

sudo umount /dev/hda1

```

(Substitute your results for /dev/hda1)

Then you should be good to go.

-merlin

---

### Post by merlinus on 2007-06-19
> **Pumalite said:**
> If Windows is Vista, you have to partition FROM Vista.

Geez....  I ALWAYS forget to ask if it's vista..... 'cuz it is so far removed from my consciousness.

The only vistas for me are tall mountains.....

Thanks!

-merlin

---

### Post by ubun7upanz3r1337 on 2007-06-19
Hopefully that should work, i think it should because it says that it was mounted from the command line.

---

