---
title: "ntsf-config doesn't work"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by m5b on 2008-02-17
After installing Ubuntu 7.10 I cannot write to an external hard drive on which I have installed 3 NTSF Windows partitions, no can I write to the Windows partiton my hard drive. Previous posters with this problem were told to install ntsf-config and to run it. I installed ntsf-config but when I run this program it asks only if I want to enable write to an external and/or internal drive(s). Regardless of what I specify, the program says that it is doing something to the internal drive (only), but I am still unable to write to either my hard (internal) drive or to my external drive.

---

### Post by jan quark on 2008-02-17
run this installation code

```
sudo apt-get install ntfs-3g ntfsprogs
```

then please run these terminal commands and post the output here 
thank you

```
mount
```

```
sudo fdisk -l
```
```

cat /etc/fstab
```

---

### Post by m5b on 2008-02-17
I did what you suggested, but the output was huge. I am not sure how to transfer the output (without typing it all) to a message that I can send to you.

The inaccessible (for writing) partitions remain inaccessible after I entered the commands you suggested.

---

### Post by m5b on 2008-02-17
I did what you suggested, but the output was huge. I am not sure how to transfer the output (without typing it all) to a message that I can send to you.

The inaccessible (for writing) partitions remain inaccessible after I entered the commands you suggested.

---

