---
title: "Using dd to copy a SINGLE partition"
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by BetterSense on 2008-08-11
I have a full 320gb hdd with two partitions, as small root, and a big home.

I have a 1TB new hdd that I created two partitions as well, both bigger than the old ones. I formatted it ext 3.

From a liveCD I copied my whole /home from my old hdd to the new hdd. 

Now, I wanted to copy the whole root over. But, it doesn't work becaues of weird files like /proc. So, I tried using dd

```
sudo dd if=/dev/sda1 of=/dev/sdb1
```

This should have copied the small partition of the 320gb drive (with my install on it) to the small partition of the new drive (with nothing on it). Right? I wasn't quite sure what happens if you dd a partition to a larger partition. But, in any case, I mount /dev/sdb1 and it's empty, when it should have all my install on it. Any other ideas on how to transfer my install over to this new hdd would be appreciated.

---

### Post by munkyeetr on 2008-08-11
1) Boot to a LiveCD and make sure the drive you want to copy is unmounted.
2) Use the following command to save it as a drive image:
```

dd if=/dev/sda1 of=/dev/sdb1/imagename.img

```

---

### Post by heyyall714 on 2008-08-11
May I humbly suggest dd-rescue - comes stock on the gparted live CD which has been a lifesaver.

[http://www.gnu.org/software/ddrescue/ddrescue.html]("http://www.gnu.org/software/ddrescue/ddrescue.html")

-w

---

### Post by BetterSense on 2008-08-11
> **munkyeetr said:**
> 1) Boot to a LiveCD and make sure the drive you want to copy is unmounted.
2) Use the following command to save it as a drive image:
```

dd if=/dev/sda1 of=/dev/sdb1/imagename.img

```

ok, so then you are creating a *file*, on the sdb1 partition? Is that just going to work? Is it what I needed to do in the first place?

If I did that it seems like that creates an image file, sitting on /dev/sdb1. I'm confused as to what that is going to do. Work, possibly, but I would like to understand what is happening. 

I just want to effectivly move my installation to the new hdd. You are suggesting that I make an image file of my whole root partition and put it on my new root partition. How is that going to work when I run the system, and it needs to save more stuff, and stuff? What exactly is an image file, is it just a folder with a whole file tree in it? Sorry maybe I should have posted in the noob forum.

> May I humbly suggest dd-rescue
cool, but what would I do with it? Does it have a 'copy your partition to another bigger partition on your new hard drive' option or something?

---

### Post by munkyeetr on 2008-08-11
sorry, i misread and was under the impression that you wanted to create a backup of the drive, which creating the image would do.

---

### Post by BetterSense on 2008-08-11
That's what I thought, thanks. I found a partimage tutorial on the internets that I will try. If that fails, is it possible to reinstall, then copy, like, /bin, /usr, and /share from your old install over and have it effectively be the same? The only things keeping me from just renistalling is I had a hard time getting my scanner, my dual monitors, sound, japanese fonts all configured.

---

### Post by hotdoog on 2009-02-09
Hi, just stumbled upon this. I'm trying to use dd to restore a partition from a backed up image. Anyone know how to mount an image to RAID? (not sure if possible)

Anyway, I found this on a gentoo forum:

```
telinit 1; cp /dev/sda /dev/sdb
```

[http://www.unix.com/gentoo/30298-how-copy-single-partition.html](http://www.unix.com/gentoo/30298-how-copy-single-partition.html)

for copying a whole drive. Not sure if that works with GUI running. There are more ideas on that link.

For the record you don't need to use dd to copy a root partition and have it be functional. Various "weird" directories like /proc as you mention only contain date that is used when the system is running. I'm pretty sure it's of no importance to save for the next reboot. I've usually just used rsync instead of cp because I like all the info it gives me to make sure I'm not making a mistake. I usually use:

```
rsync -avnu --stats --progress / /mnt/newlocation
```

And I've never had problems. I even copy the boot partition this way.

As for the GRUB, Use the super GRUB disk. I am in love with this simple liveCD ever since I discovered it and I can't recommend it enough. Basically the cp command copies all the important data - all you need is the GRUB on the MBR. This is normally a kind of tricky thing to do because MBR is annoying. But with the Super GRUB CD all you do is boot the cd, select the partition where your /boot is and it writes the MBR automagically and next time you boot fine without the CD. Sometimes it is harder if you have many bootable partitions to remember the drive numbers but that is exactly when you need SUPERGRUB to help you. The GUI of supergrub is a very primative and confusing at first but once you get it it is perfect. It won't harm anything unless you have a Windoze partition to worry about. Yay SuperGRUB!:p

PS if you prefer to use cp over rsync use this:
```
cp -dpRx / /mnt/newlocation
```

which I got from:
[http://www.howtoforge.com/software-raid1-grub-boot-debian-etch-p2](http://www.howtoforge.com/software-raid1-grub-boot-debian-etch-p2)

---

### Post by moonsoup on 2011-12-31
I love pcopy!
You can find it in the dpkg repos with apt-get - you can use yum if you are on centos or redhat or you can install from source ( if like me you are on lfs ) below.
[ftp://ftp.lysator.liu.se/pub/unix/pcopy]("ftp://ftp.lysator.liu.se/pub/unix/pcopy")

 Here is a quick tutorial on how to use pcopy.
[http://ns2.rbroom.com/usr-share-doc/newbiedoc/newbiedoc.berlios.de/wiki/Cloning_a_hard_disc.html]("http://ns2.rbroom.com/usr-share-doc/newbiedoc/newbiedoc.berlios.de/wiki/Cloning_a_hard_disc.html")

I use pcopy with parted to find the exact beginnings and ends of the partition I want to copy. This way I have something exact to enter into pcopy. 
Good luck!:popcorn:

---

