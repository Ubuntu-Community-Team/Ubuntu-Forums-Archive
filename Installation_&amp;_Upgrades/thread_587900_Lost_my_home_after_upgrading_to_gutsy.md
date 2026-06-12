---
title: "Lost my home after upgrading to gutsy"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by bruzzel on 2007-10-23
After successfully upgrading to 7.10 I lost my /home which is on a separate partition. I edited /etc/fstab with a line:

/dev/sda2 /home jfs defaults 0 2

but gutsy seems to ignore it at reboot. What can I do?

Thanks

Kris

---

### Post by 1/0 on 2007-10-23
Buy a new home. Only kidding. Try mount it manually first:

```

mkdir test
sudo mount /dev/sda2 test

```

Mount as test or any other empty folder. That way you know its there. Any errors in /var/log/messages? Is home formated as jfs?

---

### Post by bruzzel on 2007-10-23
Thanks, but I already found the right answer myself, just post it back to help others: the line in fstab should read:
/dev/mapper/sda2 /home jfs defaults 0 2

It's the "mapper" part that does it, don't ask me why!

---

