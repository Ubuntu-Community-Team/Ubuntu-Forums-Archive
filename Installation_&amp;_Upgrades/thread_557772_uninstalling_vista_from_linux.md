---
title: "uninstalling vista from linux"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by Irti on 2007-09-23
hey i messed up my vista when i tried to compress the drives....is there any way i can format my windows partition from linux...(i am running ubunt fiesty)....

---

### Post by olejorgen on 2007-09-23
Installing **gparted** would probably be easiest

---

### Post by Irti on 2007-09-23
ok am gonna try that ...thanx

---

### Post by olejorgen on 2007-09-23
Remember to mark the thread 'solved' it it works. (thread tools -> mark as solved)

---

### Post by dasunst3r on 2007-09-23
Are you running a dual-boot installation?  If so, simply deleting the partition is probably going to hose your installation.  After you delete your partition, you might want to run *sudo update-grub* in the terminal.

---

