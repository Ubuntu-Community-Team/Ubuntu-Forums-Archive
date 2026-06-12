---
title: "One Last SImple Question Before I Install"
date: 2007-08-04
forum: Installation &amp; Upgrades
---

### Post by Aesir09 on 2007-08-04
[IMG]http://i71.photobucket.com/albums/i141/Bodomshadow/Screenshot-Install.png[/IMG]

**one last question AM I SHRINKING MY WINDOWS PARTITION OR CREATING A NEW ONE TO INSTALL UBUNTU ON?**

---

### Post by Pumalite on 2007-08-04
Post fdisk -l(small L) Actually, Gparted(the stand alone-burn-to-disk program) gives you much more control. Not knowing the rest is hard to answer your question with certainty.

---

### Post by Aesir09 on 2007-08-04
fdisk -l(small L)


?

---

### Post by Aesir09 on 2007-08-04
fdisk -l

---

### Post by Aesir09 on 2007-08-04
,,,,,,,,,,,,,,,

---

### Post by Pumalite on 2007-08-04
Use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
How many drives? Are you dual booting with XP or Vista? How large the hard drive? How much do you want to allocate to Ubuntu?

---

### Post by merlinus on 2007-08-04
```

sudo fdisk -l

```

-merlin

---

### Post by Aesir09 on 2007-08-04
blah no no codes right now.

puma, i only want 20g towards ubuntu.

my HDD is 117GB

whenever i put the bar all the way to the left, it reads: 51.5GB(47%)

and whenever i move it all the way to the right it reads:109GB(100%)

im pretty sure im resizing my winblows partition right

PS: my winblows partition has about 55GB left on it

---

### Post by Aesir09 on 2007-08-04
oh yes and here:



Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5       14593   117186142+   7  HPFS/NTFS

---

### Post by Pumalite on 2007-08-04
You want real control over the process? Use Gparted. It's a small download. I would also advise 'Manual'. Give 10 GB to'/', 500 MB to Sawp, and the rest to /home. If dual booting with Vista is a different story.

---

### Post by Aesir09 on 2007-08-04
gparted doesnt let me do grub thingee then does it?
plus gparted is already built in lol


```
sudo su gparted
```

---

### Post by Pumalite on 2007-08-04
Gparted lets you do everything. It's not the same program.

---

### Post by Aesir09 on 2007-08-04
ok well tell me exactly what to do please here this will help

[IMG]http://i71.photobucket.com/albums/i141/Bodomshadow/Screenshot--dev-sda-GParted.png[/IMG]

---

### Post by Aesir09 on 2007-08-04
blah i just want to do it the regular way:confused:

---

### Post by Aesir09 on 2007-08-04
all i want is 20gb, im coming back in a few hours

please just tell me what to do, during the install

20gb


thats all


im a noob this shouldnt be hard for you awesome linux geeks:lolflag:

geeks as in exp linux user not as an insult

---

