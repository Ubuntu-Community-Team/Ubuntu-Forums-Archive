---
title: "Partitioning in linux"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by shakyj on 2008-05-06
Right,
Installed nux on a 20gb hdd which was all i could find last night. Just found a spare 80 GB one and want to use that too. Whats the best way to go about it? Swap is 85mb on hda so want to make that bigger and move my user to hdb. got gparted open but not sure if i need ext2 or ext3 for my files. Or if there is a better way?

EDIT: looks like I will have to put my swap on hdb because i cant resize my ext3 on hda as its obviously mounted. Can I just make a swap partition on hdb and it will see it or do I need to do more?

---

### Post by Pumalite on 2008-05-06
You can have /swap in any of the drives and Ubuntu will see it. I use ext3, but that's a personal thing. Are you using Vista?

---

### Post by c4v3m4n on 2008-05-06
I also use ext3, it works.

---

### Post by shakyj on 2008-05-06
Nope, just got ubuntu on this pc. Got xp on my main pc as I hate vista

---

### Post by Pumalite on 2008-05-06
Good!
Here is a link worth checking:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by twright on 2008-05-06
you can use lvm to combine several physical drives into one logical volume

---

### Post by shakyj on 2008-05-06
Hmmm. got my partitons sorted.Just cant figure out how to mount my home to sdb instead of sda

---

### Post by Pumalite on 2008-05-06
Check this:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

