---
title: "Partitioning Trouble.."
date: 2007-08-05
forum: Installation &amp; Upgrades
---

### Post by Hickler on 2007-08-05
I had Ubuntu installed and then discovered Sabayon and liked it, so I tried to partition my hard drive for both of the OS's but I didn't reall know how and ended up deleting the partition and now I only have Sabayon. I like Sabayon but I miss some of the features, stability and the great community that comes with Ubuntu, so is there any way I can partition my hard drive to have both of these OS's? Thank you.

---

### Post by Pumalite on 2007-08-05
Post fdisk -l(small L). Use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
But would help to know how things look now after the 'little problem'

---

### Post by Hickler on 2007-08-05
Is this "unknown" thing normal, and what do I do now, I'm pretty sure I have the same options with gparted as I have with the Ubuntu live cd...

---

### Post by Pumalite on 2007-08-05
Use Resize. BTW, the stand alone program is newer, has more control over the process.

[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by Hickler on 2007-08-05
> **Pumalite said:**
> Use Resize. BTW, the stand alone program is newer, has more control over the process.

Where can I find the stand alone? And I can't resize the 55GiB one, just the 101MiB one...

---

### Post by maybeway36 on 2007-08-05
I can't run GParted off the live CD on computers with i815 graphics, so I use Knoppix then. GParted is included, although I'm not sure how new it is.
As for partitions, I'd recommend two ext3 partitions (one for each OS) and a swap partition.

---

### Post by Hickler on 2007-08-05
> **maybeway36 said:**
> I can't run GParted off the live CD on computers with i815 graphics, so I use Knoppix then. GParted is included, although I'm not sure how new it is.
As for partitions, I'd recommend two ext3 partitions (one for each OS) and a swap partition.

So I'd have to re-install Sabayon?

---

### Post by Hickler on 2007-08-05
Does this look about right?

---

### Post by Pumalite on 2007-08-05
What is that small 'unallocated' space in the middle?

---

### Post by Hickler on 2007-08-05
> **Pumalite said:**
> What is that small 'unallocated' space in the middle?
No idea, just appeared there when I made the swap partition...

---

### Post by Pumalite on 2007-08-05
Looks ok to me. Go ahead.

---

### Post by Hickler on 2007-08-05
I'm in the Ubuntu install menu and when I try to continue after the manual partition it says 

"No root file system is defined.

Please correct this from the partitioning menu."

What do I do?

---

### Post by merlinus on 2007-08-05
Select the ext3 partition, edit, and riight-click on it and set mount point as /

-merlin

---

