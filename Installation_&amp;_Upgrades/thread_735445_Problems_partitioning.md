---
title: "Problems partitioning"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by SeanONeil on 2008-03-25
I'm in the middle of installation, and I'm stuck on the partitioning section of it (page 4). I was looking at the graphic install at the Ubuntu page, and my installation skipped through a few screens and is now at a 'prepare partitions' page, which is just a blank box. It says I need to 'specify a root file system', and some other stuff. Do I need to have windows installed on an internal hard drive in order to get this to work, or is ubuntu just not recognizing my hard drive? It's a western digital SATA 500 gig. Also - AMD 64 Athlon x2, asus SLI M2N mobo.

Thanks in advance!

:confused:

---

### Post by Pumalite on 2008-03-25
Western Digitals might be a problem. Post:
sudo fdisk -lu

---

### Post by Pumalite on 2008-03-25
You could also get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Check if it sees your drive.

---

### Post by SeanONeil on 2008-03-25
Thank you. Downloading now!

---

### Post by SeanONeil on 2008-03-25
> **Pumalite said:**
> Western Digitals might be a problem. Post:
sudo fdisk -lu

Also; how is this done? I'm a total linux noob, so any help would be appreciated. I've been on windows me whooooole life.

---

### Post by SeanONeil on 2008-03-26
Puma, you're going to love me for this.

Noob mistake number one.

The damn thing was unplugged.

---

### Post by Pumalite on 2008-03-26
That's a new one! Good you are up and running.

---

