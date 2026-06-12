---
title: "recover previous ubuntu installation"
date: 2007-07-23
forum: Installation &amp; Upgrades
---

### Post by mickey0 on 2007-07-23
hello,
Unfortunately I started a Debian base installation on an Ubuntu partition. At the end grub says that partition is damaged. Is there any possibility of recover ubuntu installation and my datas on that partition????
If I install again ubuntu on that partition without format it, wil the partition be recover? (I need don't lose my datas and packages configuration).

thanks

---

### Post by phidia on 2007-07-23
I don't think trying to install on the partition will get your data back, you can try the no format option but I haven't seen that work particularly in the situation you're describing. 
I think your best chance at recovering the data is to boot with a live cd e.g knoppix, ubuntu, dyne:bolic (there are many others) and try to mount the partition and then copy your data _if_ you can even see it.

---

### Post by mickey0 on 2007-07-23
I tried with Ubuntu live and I can't mount the partition........it can't access to it. It gets an error.

---

### Post by phidia on 2007-07-23
> **mickey0 said:**
> I tried with Ubuntu live and I can't mount the partition........it can't access to it. It gets an error.

That's a bad sign-I'm sorry to say. There are ways to retrieve data from a drive but it's not easy or inexpensive.

---

### Post by mickey0 on 2007-07-23
hi, the message appears when I try  access to every partitions because my fstab files contains only line swap partition! How can I create a new fstab file???

---

### Post by phidia on 2007-07-23
if you're running from a live cd you shouldn't need to create a new fstab.
You need to make a mount point e.g. sudo mkdir /mnt/hdx,x
Then type sudo mount /dev/hdx,x /mnt/hdx,x <enter>
Where I have an "x" you will have to insert the correct values for partition.
Hope that's helpful.

---

### Post by mickey0 on 2007-07-24
yes, but the message appears when I launch pc with ubuntu disk. Konqueror show me partitions Icon but every access to they gets that error.....

---

### Post by phidia on 2007-07-24
> **mickey0 said:**
> yes, but the message appears when I launch pc with ubuntu disk. Konqueror show me partitions Icon but every access to they gets that error.....

Could you post the error message exactly as it appears?
If it's some thing like > mount: can't find /dev/hda1 in /etc/fstab or /etc/mtab
Then linux/ubuntu doesn't recognize the filesystem type which means that partition is probably lost.

---

