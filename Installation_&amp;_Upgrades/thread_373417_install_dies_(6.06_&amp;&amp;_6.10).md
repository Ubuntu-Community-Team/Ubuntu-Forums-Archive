---
title: "install dies (6.06 &amp;&amp; 6.10)"
date: 2007-03-01
forum: Installation &amp; Upgrades
---

### Post by PlaHPoy on 2007-03-01
I have tried both 6.06 and 6.10 live cd's (amd64 versions).  I start the installation process on 6.10 and it exits after initializing fsck 1.39.  Just hangs / dies and im out to a black blank console.  I am getting the EXACT same error as this [http://ubuntuforums.org/showthread.php?t=365656&highlight=fsck+1.39](http://ubuntuforums.org/showthread.php?t=365656&highlight=fsck+1.39) .  

my specs are :
amd64 3400+
512 ram
60gb hd
nvidia 7950 gt
chipset: NF4
dvdrw

thats pretty much it.... I was under the impression ubuntu was supposed to be one of the most beginner friendly distros out there, is this a common problem?

thanks to anyone in advance

Zach M.

---

### Post by angryfirelord on 2007-03-01
Well, nobody's perfect, and it's hard to make one OS that will run on almost every single piece of hardware.

If the desktop installer doesn't seem to work, then you try the Ubuntu alternate install. It's not as friendly (text mode), but if you read carefully, it's not that difficult either.

If the installer still wants to execute fsck, then what you could do is get an ISO of GParted, burn it, and use it to wipe out any existing Linux partitions. Then, when you boot the desktop or alternate install, it should work.

---

### Post by PlaHPoy on 2007-03-01
so the problem is that the HD isnt clean?

---

### Post by angryfirelord on 2007-03-01
I'm not too sure, but do you have any linux partitons on your hard drive?

---

### Post by PlaHPoy on 2007-03-01
none

---

