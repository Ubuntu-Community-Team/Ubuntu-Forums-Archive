---
title: "Hardy No Automount unless I browse the ntfs drive"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by Jammerdelray on 2008-05-05
Ok so when I login to hardy, my ntfs partiton icon is not showing on the desktop unless I double click the ntfs partition in Nautilus, same with reboots. I'm not too experienced with Terminal Commands yet. 

I did "sudo fdisk -l" see the screenshot below.

---

### Post by Pumalite on 2008-05-05
Post:
cat /etc/fstab

---

### Post by Jammerdelray on 2008-05-05
Ok here it is.

---

### Post by Pumalite on 2008-05-06
Can't see anything. You need to edit fstab and add a line for Windows using the same syntax (add ntfs-3). Get the UUID from:
blkid

---

### Post by christophski on 2008-05-06
I use a program called something like NTFS-3G configuration. Look in Add/Remove and it will be there, just search for NTFS.
Just run the program and it will have a little wizard type interface. After rebooting, your NTFS drive will automount.

---

### Post by Jammerdelray on 2008-05-06
OK got it fixed, thanks guys.

---

