---
title: "Installed hardy on Thinkpad, Windows not bootable now"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by konungursvia on 2008-06-28
Yikes! I'm scared, it's my wife's laptop from work. It has / had Win xp pro on it, I tried to install Fedora 8, it couldn't partition the ntfs drive. I tried Hardy, my favourite, and it could partition the ntfs drive, but only if I "used a new partition table". It said this was reversible. So I installed it using the last 10% or 10Gb of the drive, and foolishly told the installationo "not to use the ntfs partition". So it worked, I could boot Ubuntu from grub. 

Ah, but where was Windows? Nowhere in grub. I tried Gparted but it could do *nothing* with the ntfs partition remaining there. So I tried the Hardy disk again, and thought, why not *reinstall* hardy on the same newer 10Gb partition, but this time telling the partition manager to "use" the larger partition and have its mount point at /windows, but still not formatting it. 

I reinstalled Hardy, but still no Windows in the grub menu. So I tried the same thing, reinstalling it again. This time I think I reformatted the ntfs drive, but it only took 1 sec, so I think it just "deemed" it reformatted.

Now I don't know what to do. Even super grub disk is unable to read the former windows files, which are magnetically still there, I am sure. 

Please help!

---

### Post by Pumalite on 2008-06-28
Post:
sudo fdisk -lu

---

### Post by konungursvia on 2008-06-28
Supergrub disk messed up even the linux install, so I'll put it back on the small partition and then post that fdisk result. Thanks.

---

### Post by Pumalite on 2008-06-28
You can do it with any Live CD you might have.

---

### Post by konungursvia on 2008-06-28
I have tried live cds, but the ntfs partition thinks it is empty, so I have to unformat the partition somehow.

---

### Post by Pumalite on 2008-06-28
Use TestDisk and check your Partition Table:
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by konungursvia on 2008-07-01
Fixed, thanks. My wife took an image of the whole drive and restored it.

---

