---
title: "adding a swap partition"
date: 2006-09-02
forum: Installation &amp; Upgrades
---

### Post by Vinger on 2006-09-02
Hello,

I'm using Kubuntu 6.06 for some time now, and by reading a lot, i found it was better to use a swap partition, which i don't do...

There is a partition on my harddrive that isn't used, and that i can reformat without problem...

How do i start adding a swap partition?

tx
grz

---

### Post by taurus on 2006-09-02
Okay, assuming that it is /dev/hda3, open a terminal and do

```

sudo mkswap /dev/hda3
sudo swapon /dev/hda3 
free <-- it should show swap on it...

```
Then, you want to add that to your /etc/fstab so it will be mounted automatically upon boot...

```
sudo nano /etc/fstab
```
Add this line in there...

```

/dev/hda3   none   swap   sw   0   0

```

---

### Post by Vinger on 2006-09-02
and what is the best volume i can take?
1GB? 0.5GB 2 GB?

---

### Post by taurus on 2006-09-02
Best volume!!!  I assume you mean the best swap partition size!  512MB should be enough but 1GB even better.  No need to go more than 1GB for swap...

---

