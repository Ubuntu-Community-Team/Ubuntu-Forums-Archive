---
title: "Dual booting XP64 + Kubuntu 7.10"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by Arken on 2008-01-03
I am installing Kubuntu 7.10 on my new system, and this is what I want partitioned:

1. 100 GB Storage
2. 30 GB windows
3. 5 GB Temp
4. 25 GB Kubuntu.

I have this for mount points


1. ( I need the mount point)
2. ( I need the mount point)
3. /tmp
4. /

Also, they are type ext3. Should I change that?
Am I doing this right, and also, what do I fill in for the first two?
Thank you.

---

### Post by Arken on 2008-01-03
Bump. I need help.

---

### Post by Pumalite on 2008-01-03
Use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk amd boot from it.
1.-10 GB for '/'
2.-1 GB for /swap
3.-The rest for /home.
This is all you need.

---

### Post by Arken on 2008-01-03
Hmm. Are you sure? I wanted 4 different partitions.. from the looks of what you said, I would only have 3... I'm a noob when it comes to linux so excuse my stupidity :\

---

### Post by Pumalite on 2008-01-03
Don't worry. Do as I say and you'll be fine. Remember to backup everything before the installation. This is a matter of good practice with the installation of any new OS.

---

