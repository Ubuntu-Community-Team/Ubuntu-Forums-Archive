---
title: "Delete all linux kernel headers"
date: 2011-09-19
forum: Installation &amp; Upgrades
---

### Post by matheusramos on 2011-09-19
Hi,

I removed, unintentionally, all linux-kernel-headers using synaptic and my system don't boot anymore. Exist anything i can do to restore my system?

I use Ubuntu 11.04. Restore grub doesn't work.

Thank you

---

### Post by i.r.id10t on 2011-09-19
Kernel headers aren't required for booting... did you perhaps also remove the kernel itself?

---

### Post by sisco311 on 2011-09-19
Well, if you removed the kernel, you can boot a Live CD/USB, chroot into the installation and reinstall it.

Follow the instructions from: [uhelp]community/Grub2#ChRoot[/uhelp]

At step 6 bind the resolv.conf file:
```
sudo mount -B /etc/resolv.conf /mnt/etc/resolv.conf
```

Instead of steps 8, 9 and 10 install the kernel:
```
sudo apt-get update
sudo apt-get install linux-image-generic
```

---

### Post by matheusramos on 2011-09-20
Unfortunately i do not saw the sisco311 post. But i did which he say:

I boot on liveCD and execute the following commands:

```
mount /dev/sda6 /mnt
mount -t proc none /mnt/proc
mount -o bind /dev /mnt/dev
```

After that:

```
sudo chroot /mnt
```

(i don't know why, but i execute this command to got internet access)

```
sudo dhclient wlan0
```

install the needed packages

```
sudo apt-get update
sudo apt-get install linux-headers-$(uname -r)
sudo apt-get install linux-image-generic
```

And restore my grub2 with help of this tutorial (and with help of my friend Renê):
[http://www.taringa.net/posts/linux/10564223/Recuperar-GRUB-2-en-Ubuntu-11_04.html](http://www.taringa.net/posts/linux/10564223/Recuperar-GRUB-2-en-Ubuntu-11_04.html)

Thank you guys!

---

### Post by sisco311 on 2011-09-20
Cool! Don't forget to mark this thread as SOLVED.

---

### Post by MAFoElffen on 2011-09-20
> **i.r.id10t said:**
> Kernel headers aren't required for booting... did you perhaps also remove the kernel itself?
??? No they are not BUT --> The present kernel's linux header files ARE REQUIRED for updates and installations of certain packages. 

Some people purge past kernels and their respective header files.  I like to help people with graphics issues and I consider it a bug when the linux header files are not installed and present...  To prevent some problems from arising, you might want to ensure you have a complete set of what is current for your install.

---

