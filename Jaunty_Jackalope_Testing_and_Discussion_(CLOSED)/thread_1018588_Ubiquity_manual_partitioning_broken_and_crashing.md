---
title: "Ubiquity manual partitioning broken and crashing"
date: 2008-12-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Starks on 2008-12-22
This is absolutely unacceptable.

---

### Post by Bou on 2008-12-22
I also noticed it, but I can't see why it should be unacceptable. It's an alpha, after all.

---

### Post by Starks on 2008-12-22
> **Bou said:**
> I also noticed it, but I can't see why it should be unacceptable. It's an alpha, after all.

Unacceptable because I can't place my /home on a separate partition without using Intrepid.

---

### Post by Starks on 2008-12-22
Oh boy. How annoying, the Intrepid LiveUSB partitioner doesn't even work, period, unless I force a dismount.

---

### Post by ronacc on 2008-12-22
so whats new ubiquity has never worked worth a darn for me .

---

### Post by Bou on 2008-12-22
> **Starks said:**
> Unacceptable because I can't place my /home on a separate partition without using Intrepid.

I used the alternate CD and got it working. It's annoying as hell alright, but it *can* be done.

---

### Post by Starks on 2008-12-22
I'd do as you suggested, but I still avoid command line whenever I can.

---

### Post by Bou on 2008-12-22
Let's hope it gets fixed shortly, it is a nuisance indeed. Do you know if there's a bug filed?

---

### Post by Starks on 2008-12-22
> **Bou said:**
> Let's hope it gets fixed shortly, it is a nuisance indeed. Do you know if there's a bug filed?

Not sure, a cursory glance at the launchpad entry would suggest not.

---

### Post by jerrylamos on 2008-12-22
I filed bug #310671.  It's been broken for several consecutive daily builds.  Anyone have any clue what the developers are trying to do?  

Jerry

---

### Post by naught101 on 2008-12-23
> **Starks said:**
> Unacceptable because I can't place my /home on a separate partition without using Intrepid.

Er, you can  (I assume you have an existing /home partition, otherwise you could just create a new one):

[LIST=1]
[*]Just delete the / partition, and recreate it. 
[*]You can leave swap, since it works without a mount point. 
[*]Ignore the /home partition, and continue installing.
[*]Boot, and add /home to /etc/fstab (you can grab the appropriate line from your old fstab before you format /)
[*]rm -rf /home/* /home/.??*
[*]reboot.
[/LIST]

---

