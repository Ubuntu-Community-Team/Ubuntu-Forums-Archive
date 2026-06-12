---
title: "how to mount MS FAT floppy"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by hill0093 on 2007-02-23
I have just installed linux and am trying to learn basic things.
I need the exact mount command and procedure so I will be able to copy a text file to a Windows floppy and print it on a printer that is on an XP computer.
I cannot understand "man mount" output.

---

### Post by taurus on 2007-02-23
Applications -> Accessories -> Terminal
```
sudo mount -t vfat /dev/fd0 /media/floppy -o iocharset=utf8,umask=000
```

---

### Post by hill0093 on 2007-02-23
I did that and it rplies with "/dev/fd0 is not a valid block device".

---

### Post by taurus on 2007-02-23
Can you post this output from a terminal?

```
cat /etc/fstab
```

---

