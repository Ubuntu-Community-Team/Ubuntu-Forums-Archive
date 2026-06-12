---
title: "Fsck Grub troubles errors 2 and 17"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by jimjag on 2008-06-20
I originally bought my computer that had Vista installed but repartitioned a section of it and installed ubuntu 8.04.
I decided last night to shrink my windows partition further to increase the space on my linux partition (ext3)

I used paragon partition magic 8.5 to redistribute the free space on my windows partition.
when i rebooted i recieved linux error saying that i needed to run fsck, unfortunately my charger had fallen out mid partition and my computers battery ran out mid fix.

now when I try to reboot I get a "loading 1.5 ... error 2" with the grub I was sure that this had something to do with te linux partition having it's sectors stuffed up so i booted up the live cd and tried to access the linux partition but it failed to mount and i got an error 17.

How do I run Fsck???? just wondering???

---

### Post by VMC on 2008-06-20
> **jimjag said:**
> I originally bought my computer that had Vista installed but repartitioned a section of it and installed ubuntu 8.04.
I decided last night to shrink my windows partition further to increase the space on my linux partition (ext3)

I used paragon partition magic 8.5 to redistribute the free space on my windows partition.
when i rebooted i recieved linux error saying that i needed to run fsck, unfortunately my charger had fallen out mid partition and my computers battery ran out mid fix.

now when I try to reboot I get a "loading 1.5 ... error 2" with the grub I was sure that this had something to do with te linux partition having it's sectors stuffed up so i booted up the live cd and tried to access the linux partition but it failed to mount and i got an error 17.

How do I run Fsck???? just wondering???

From the livecd. Something in the order of

```
fsck -pcfv /dev/sdb1
```


But first output these:

```
sudo fdisk -l
cat /boot/grub/menu.lst
cat /etc/fstab
```

the /boot must be the /boot of your installed ubuntu not livecd

---

### Post by jimjag on 2008-06-20
I'm running the check and repair option at the moment through the Partition editor that comes on the live cd.

When/if it finishes, if it's still not working i'll do what you say in your post.

---

