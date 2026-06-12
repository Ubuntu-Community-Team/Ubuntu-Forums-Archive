---
title: "Fatal deletion of my boot record via GZip"
date: 2010-01-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by k64 on 2010-01-25
When I tried to GZip my root drive to creat a boot chart and closed the terminal because it wasn't responding, I actually erased my root drive! This is a fatal bug with GZip in Lucid Lynx that needs to be taken care of. I am currently reinstalling Lucid Lynx right now, but I am posting this to help keep others from reaching this deadly fate.

---

### Post by mdurham on 2010-01-25
> When I tried to GZip my root drive to creat a boot chart
How does GZip create a boot chart? I'm just curios.

---

### Post by Seventh Reign on 2010-01-25
Something fishy about this...

---

### Post by VMC on 2010-01-25
Yea, I agree. Somethings strange here. Do we have the full story?

Were you in the same file system that you were trying to compress, or did you do it from another file system?

---

### Post by gnomeuser on 2010-01-25
[https://wiki.ubuntu.com/BootCharting](https://wiki.ubuntu.com/BootCharting)

Which step calls for compressing / again?

---

### Post by k64 on 2010-01-26
A boot chart is a .tgz file. That's what I tried to create of my entire hard drive, only to brick Lucid.

---

### Post by lisati on 2010-01-26
> **k64 said:**
> A boot chart is a .tgz file. That's what I tried to create of my entire hard drive, only to brick Lucid.

According to [this]("https://wiki.ubuntu.com/BootCharting") the bootchart is a png file, not a tgz file.

---

### Post by ranch hand on 2010-01-26
bootchart is a .tgz file.  pybootchart is a gui app that creates the .png file.  YOu can open the .tgz file and wade trough an awful lot of data and get the same results as the .png.  It just will take you half the day.

pybootchart is installed automatically when you in stall bootchart.  This is simple to check in synaptic.

---

### Post by lisati on 2010-01-26
Possibility: maybe the OP got hold of a tgz file of the bootchart stuff, and, because of a typo, ended up with gzip trying to add the contents of his hard drive the tgz file instead of extracting it.......

---

### Post by k64 on 2010-01-26
> **lisati said:**
> Possibility: maybe the OP got hold of a tgz file of the bootchart stuff, and, because of a typo, ended up with gzip trying to add the contents of his hard drive the tgz file instead of extracting it.......

Actually, here's the command:

```
gzip -R / ~/bootchart.tar.gz
```

This essentially explains what I was trying to do.

---

### Post by Starks on 2010-01-26
Why would you do that? All you had to do was make sure pybootchartgui was installed and then check /var/log/bootchart after 2 reboots (first reboot runs ureadahead).

---

### Post by Paqman on 2010-01-26
```
gzip -R / ~/bootchart.tar.gz
```

Wow. You packed your entire filesystem into an archive?!? Why? Were you following a HOWTO? If so can you tell us where you got it from, because somebody has _seriously_ misled you.

---

