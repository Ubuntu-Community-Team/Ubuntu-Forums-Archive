---
title: "How to perform Non destructive Reinstall?"
date: 2007-09-21
forum: Installation &amp; Upgrades
---

### Post by csf111 on 2007-09-21
Swapped disks from one machine to the other.
Now need to reinstall so the appropriate video,
sound, network, etc., drivers,get loaded. 

BUT I don't want my data (30G) hosed!

Saw this append, (with limited suggestions) and this is what I am looking for:

In Windows if you use "Setup" you can reload the OS and leave your pre-existing files and data intact. This option just overwrites the 'important' system files and whatever original drivers and registry values from the original disk, while allowing any system changes (added software, hardware, customizations, etc.) to be preserved.

Any thoughts appreciated.

---

### Post by Pumalite on 2007-09-21
Transfer your 30 GB of data to an external drive. That way you will always have it safe.

---

### Post by maybeway36 on 2007-09-21
Use a seperate /home partition next time.

---

### Post by csf111 on 2007-09-21
What would that do? 

(When I install, just ignore that partition?)

How would you partition a 250G drive?

---

### Post by Pumalite on 2007-09-21
Save your data, Then get Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Delete all partitions you have (assuming you are not dual booting) and then make one large partition of your hard drive, format ext3 if you want, then install; go manual and assign 10 GB to '/', 500 MB to /swap, the rest for /home.

---

### Post by csf111 on 2007-09-21
...hmm, ok, got it.

SO, it would be possible to create a /HOME,
and transfer the contents of my exisiting
HOME (directory) to it? 

Do I need GPARTED for that? Or is there some
kind of other tool I could use?

---

### Post by Pumalite on 2007-09-21
Gparted (the stand alone, burn to CD, boot from, program) is the best partitioner around. Period.

---

### Post by csf111 on 2007-09-21
Thank you

---

### Post by Pumalite on 2007-09-21
You are welcome. Good luck.

---

