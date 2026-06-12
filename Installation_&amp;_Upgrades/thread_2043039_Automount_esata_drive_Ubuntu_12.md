---
title: "Automount esata drive Ubuntu 12"
date: 2012-08-15
forum: Installation &amp; Upgrades
---

### Post by Monosabio on 2012-08-15
Hi, I've beeing struggling for the past few days with a fresh Ubuntu 12 (re)installation. Now my eSata drive is not mounted automatically when connected (powered on). 
The question is how can Ubuntu detect the eSata drive as it does when you connect an USB drive. The previous Ubuntu 12 installation (running on the same box) worked as charm. I eventually can mount the esata drive by adding into /etc/fstab the corresponding configuration (UUID=4B7E59724F69E3F8	/media/eSata	ntfs	defaults,nls=utf8,umask=0222	0	0) and then type sudo mount -a.
But the problem with this is that if I boot with the eSata powered off it gives me an Warning error telling that the drive is not present and the boot sequence doesn't continue until I press the 'S' key. And that's certainly annoying. 
Can someone give me a clue ?

Thanks in advance,
Gaston

---

### Post by leclerc65 on 2012-08-15
I would install **ntfs-conf** then run it (once).

---

### Post by Monosabio on 2012-08-15
Thanks leclerc65, what the ntfs configuration tools actually do is add a new line to /etc/fstab file. Thats works fine , but the problem is when the esata (external drive) is powered off, as it is most of the time , I get a Warning message that halts booting process until I press 'S' key to continue. Before , on my previous Ubuntu 12 it was working, I suppose I did something to make it work but I can't remember.

Thanks

---

