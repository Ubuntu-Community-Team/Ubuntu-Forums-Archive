---
title: "Migrate Wubi install"
date: 2011-07-05
forum: Installation &amp; Upgrades
---

### Post by lvermei on 2011-07-05
Hi,
How do I migrate my Wubi install? When I follow [this]("http://ubuntuforums.org/showthread.php?t=1519354") guide I find myself at the problem that I don't have SDA-1 to SDA-6. I only have:
[IMAGE]("http://imageshack.us/photo/my-images/26/screenshotvxk.png/")

How do I fix this? As you already concluded, I am a total linux noob, but I guess I'll need to partition or something like that. Because I can't migrate to a disk that is in use right?

Thanks!

---

### Post by dino99 on 2011-07-05
do a fresh install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by lvermei on 2011-07-05
Oeps, I forgot to tell you I don't have a CD player. Also, my computer (HP mini 2311) doesn't have a USB startup... 

Is there any hope? I saw on the Gparted site you could use your HD as well, but it seems quite hard to me. As I said, I'm a noob :P

---

### Post by bcbc on 2011-07-05
Windows vista/7 are able to partition the hard drive while in use. In XP you'd have to see if you could download something that would do it.

Here's a method of booting an Ubuntu CD from the hard drive using grub2: [http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

I would caution you:
1. partitioning can cause loss of data so you should back up everything first
2. if you can't boot a recovery CD, then you will be unable to fix problems later (even a computer with just Ubuntu on it could have boot problems e.g. after an upgrade; it's even more likely with a dual boot scenario).

---

### Post by lvermei on 2011-07-05
Hmm. I'm not really worried about the data, it's a reset for my dad so everything has to get lost. Especially Windows.

But the tread you recommended seams awfully difficult to me... It surely must be easier to install a fresh Ubuntu if you don't care about the data? I can't imagine that it's so hard!

---

### Post by bcbc on 2011-07-05
It's simple if you have a CD drive or can boot from USB...

How about this... install Wubi to C: (/dev/sda1) instead of on /dev/sda2 (assuming you installed it on /dev/sda2, if not great).

Now when you boot Wubi, /dev/sda2 won't be mounted. You can go into gparted and format it to ext4. Then you migrate to /dev/sda2 using the [wubi migration howto]("http://ubuntuforums.org/showthread.php?t=1519354") you linked to in your first post.

Then you can boot the ubuntu on /dev/sda2 instead of the Wubi. Now you have /dev/sda1 unmounted. You can either resize the partition to keep both Windows and Ubuntu, or format it and move the Ubuntu install to it. (That wubi migration also moves regular Ubuntu intalls). If you wiped windows, then you can just manually setup /dev/sda2 as a swap partition. Simple? (Not really, but it should work).

This assumes that the 9GB on /dev/sda2 (if I calculated correctly) is enough to migrate your Wubi install. If you're using more than 9GB then it won't work. The migration script will stop you if it's not enough. In that case, delete your files, or reinstall (a fresh wubi install only uses 2.6GB)

---

