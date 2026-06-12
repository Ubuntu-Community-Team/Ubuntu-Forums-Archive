---
title: "2 drives - Partitioning?"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by jfm30204 on 2008-04-15
I'm going to install Ubuntu server and would like advice on partitioning. The computer has 2 drives:

10 G - NTFS, Windows 2000 Server system files and programs
120 G - NTFS, data

Ideally, drive 0 would have Ubuntu system files, and drive 1 would be for web sites, but I don't know if 10 G is enough, especially if I install Ubuntu Desktop on top of the server. I would appreciate any suggestions as to partitions.

Once I have decided how I want to partition the drive(s), would it be better (easier, less confusing?) to do it beforehand with GParted Live CD?

Jere

---

### Post by Pumalite on 2008-04-15
Gparted Live CD is the way to go. 10 GB is too little I think.
[http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704)
[http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10)

---

### Post by jfm30204 on 2008-04-15
Okay, I'm going to back up a bit. I have a 60G drive lying around, so I think I'll leave my Win file system intact on the 10G drive and replace it with the 60G unit. Now, using GParted live cd, how should I partition the  drives so as to have Ubuntu on hd0 and sites on hd1?

hd0 - 60G
hd1 - 120G

Jere

---

### Post by Pumalite on 2008-04-15
You mean a separate /home in hd1?

---

### Post by jfm30204 on 2008-04-15
> **Pumalite said:**
> You mean a separate /home in hd1?

Correct.

---

### Post by Pumalite on 2008-04-15
In hd0 you would need only maximum 20 GB for '/' and maximum 2 GB for /swap. Waht do you want to do with the rest?

---

### Post by jfm30204 on 2008-04-15
> **Pumalite said:**
> In hd0 you would need only maximum 20 GB for '/' and maximum 2 GB for /swap. Waht do you want to do with the rest?

No idea. I will be running a few php/mysql  sites, like Coppermine. Where does mysql space go? Suggestions?

---

### Post by Pumalite on 2008-04-15
I suggest you partition hd0 with Gparted this way:
15 Gb for '/'
2 GB for /swap
The rest for /home
Keep hd1 for storage or other purposes.
msql settings probably go in /home.

---

### Post by jfm30204 on 2008-04-15
> **Pumalite said:**
> I suggest you partition hd0 with Gparted this way:
15 Gb for '/'
2 GB for /swap
The rest for /home
Keep hd1 for storage or other purposes.
msql settings probably go in /home.

Thanks, but the one drive won't be enough space for the photo gallery which will have hundreds of large photos. Going to put my HS alma mater's yearbooks online, so, you can see that I'm going to need the larger drive, and maybe even replace it w/i 6 months to a year with an even larger one.

---

### Post by Pumalite on 2008-04-15
Then use Gparted and make the '/' partition and /swap partition in hd0 and point to hd1 and make the /home partition. Install your Server and point to the already prepared partitionsw. The space left in hd0 you can format and use as you wish.

---

### Post by jfm30204 on 2008-04-15
What would you think about a /share partition for use with Samba?

---

### Post by Pumalite on 2008-04-15
Sounds good.

---

