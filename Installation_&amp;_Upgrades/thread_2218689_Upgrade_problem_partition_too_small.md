---
title: "Upgrade problem: partition too small"
date: 2014-04-21
forum: Installation &amp; Upgrades
---

### Post by Istvan D on 2014-04-21
Hi,

I have a problem when upgrading from 13.10 to 14.04: I have a triple boot (Mac 10.9 + Win 7 + 13.10) on a Macbook with a 120GB SSD. The Ubuntu is on sda6, btrfs, 15GB. GParted says 2,9GB are free, but Baobab sees only around 4GB occupied. Why is there such a huge difference? I do not have any subvolumes, and no snapshots as far as I can see. Any ideas?

---

### Post by bkline on 2014-04-21
Is it possible you're experiencing the same issue described in this (invalid) bug report?

[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/922551](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/922551)

---

### Post by Istvan D on 2014-04-23
I do not think so, Baobab reports the correct size on the main screen, just in the analysis screen it report less:
[https://drive.google.com/folderview?id=0B5_etOeQ4anCTDkzUHVWd1VFc28&usp=sharing](https://drive.google.com/folderview?id=0B5_etOeQ4anCTDkzUHVWd1VFc28&usp=sharing)
Output of ```
sudo btrfs filesystem show /dev/sda6
Label: none  uuid: 82579bc5-a31c-478e-9ed6-4c3c3fd3566f
	Total devices 1 FS bytes used 11.70GB
	devid    1 size 14.90GB used 14.90GB path /dev/sda6

Btrfs v0.20-rc1
```
And of ```
sudo btrfs filesystem df /
Data: total=12.87GB, used=11.06GB
System, DUP: total=8.00MB, used=4.00KB
System: total=4.00MB, used=0.00
Metadata, DUP: total=1.00GB, used=658.52MB
Metadata: total=8.00MB, used=0.00
```
Any further ideas?

---

### Post by fantab on 2014-04-23
> Data: total=12.87GB, used=11.06GB
What is the output of:

```
df -h
```

If there are more than two old and unused kernels, that could take up the space needed for upgrade. 
Removing unused kernels can help you reclaim some of the space.
You can check with *sudo update-grub *how many kernels you have and if you want to remove those then you can do so with?
```
sudo dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge
```

Not sure why bobab sees only what it sees... I've never used the tool before. Hopefully someone will clarify.

---

### Post by Istvan D on 2014-04-25
the output of df -h is:
```
Fájlrendszer   Méret Fogl. Szab. Fo.% Csatol. pont
/dev/sda6        15G   13G  2,0G  87% /
none            4,0K     0  4,0K   0% /sys/fs/cgroup
udev            1,9G  4,0K  1,9G   1% /dev
tmpfs           387M  1,2M  386M   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            1,9G  212K  1,9G   1% /run/shm
none            100M   44K  100M   1% /run/user
/dev/sda1       197M   16M  182M   8% /boot/efi
/dev/sda6        15G   13G  2,0G  87% /home
/dev/sda4        39G   29G   10G  74% /mnt/adat

```I don't have unused kernels, I remove them when a new one comes out

---

### Post by sudodus on 2014-04-25
***df -h*** indicates that you are have totally 15GB, use 13GB and have 2GB free in the root partition.

Are there lots of files in the trashcan?
Are there lots of files in hidden directories?

Or could this be a problem because some tools are not working correctly with btrfs?

---

### Post by fantab on 2014-04-25
Since you don't have a separate '/home' partition your 'Home' is in '/' partition. It might help if you can make space in your 'Home'.
Apart from that I can't think of anything more than what *sudodus* has suggested.

---

### Post by Istvan D on 2014-06-23
shame on me: I did in fact have two snapshots from previous dist-updates, and those of course consumed up to 3-4GB each :D So deleted them an 14.04 updated like charm.
Thanks everybody and sorry for the distubance

---

