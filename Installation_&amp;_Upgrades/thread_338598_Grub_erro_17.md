---
title: "Grub erro 17"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by redsox59 on 2007-01-14
I have:
/dev/hba1 as Linux partition
/dev/hba2 as Linux swap

I've only one harddrive.

I can't think of anything I've changed with grub or the boot order or anything. I restarted the computer and before grub loaded up I get the error 17. 

Through a live cd I run fdisk -l and see my two partitions. They seem to be mounted correctly.

Im not sure what else I should do.

---

### Post by jd65pl on 2007-01-14
Could you boot using live CD and post

```
/boot/grub/menu.lst
```

---

### Post by redsox59 on 2007-01-14
It doesn't seem to exist. I must've missed something :(

---

### Post by jd65pl on 2007-01-15
It will be on your linux partition you will need to mount this partition with the live CD. Do the following.

```
sudo mkdir /mnt/linux
sudo mount /dev/hba1 /mnt/linux
cat /mnt/linux/boot/grub/menu.lst > ~/grubMenu.txt
```

Check the home directory on the live cd (not on your mounted partition) and there will be a file called 'grubMenu.txt' post this file

---

