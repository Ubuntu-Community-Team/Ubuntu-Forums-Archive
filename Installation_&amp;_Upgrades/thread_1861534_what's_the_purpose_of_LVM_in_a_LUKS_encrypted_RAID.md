---
title: "what's the purpose of LVM in a LUKS encrypted RAID6 setup? how to grow in the future?"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by alfonso78 on 2011-10-15
Hi,

I created a RAID6 out of 4 disks of 2TB each, so I have 4TB of space and 4TB of redundancy. This way I can withstand two disks failures.

Off-topic, but if you're going for RAID6, have a look at these two articles, they are quite interesting:
[http://www.techrepublic.com/blog/datacenter/raid-6-do-you-really-want-it/119](http://www.techrepublic.com/blog/datacenter/raid-6-do-you-really-want-it/119)
[http://www.zdnet.com/blog/storage/why-raid-6-stops-working-in-2019/805](http://www.zdnet.com/blog/storage/why-raid-6-stops-working-in-2019/805)

I created the RAID array using mdadm commands (there are several howtos, you can try this one for example: [http://web.archive.org/web/20091122090221/http://raid.wiki.kernel.org/index.php/RAID_setup](http://web.archive.org/web/20091122090221/http://raid.wiki.kernel.org/index.php/RAID_setup) )

then I created a partition over /dev/md0

(1st I tried with fdisk without realizing the partition would be only 2TB, so I had to recreate the partition with parted - see [http://ubuntuforums.org/showpost.php?p=11349393&postcount=1](http://ubuntuforums.org/showpost.php?p=11349393&postcount=1) )

On top of the partition /dev/md0p1 I created a filesystem and then following this howto I created the encrypted partition on top of /dev/md0p1:
[http://www.hermann-uwe.de/blog/howto-disk-encryption-with-dm-crypt-luks-and-debian](http://www.hermann-uwe.de/blog/howto-disk-encryption-with-dm-crypt-luks-and-debian)

And then an ext4 partition in the encrypted volume (why ext4? no idea. at first I wanted to use JFS, then I couldn't find some commands and decided for ext4).

for additional info, this is only the data partition, so no need to boot from it.

Finally my question:

[B]do I need an extra layer of LVM before the encryption or after the encryption? From what I understand, LVM is only useful if I want to have multiple partitions, but I don't think I need that.
Right now I'm not using LVM at all.[/B]

According to howtos, I can simply grow my RAID array changing each disk with a bigger one (see [http://h3x.no/2010/03/02/howto-increase-disk-space-in-a-mdadm-raid](http://h3x.no/2010/03/02/howto-increase-disk-space-in-a-mdadm-raid) or [http://blogging.dragon.org.uk/index.php/mini-howtos/howto-use-linux-raid-5](http://blogging.dragon.org.uk/index.php/mini-howtos/howto-use-linux-raid-5) )
and I can grow both the LUKS encrypted device (see [http://www.debian-administration.org/article/Resizing_Encrypted_Filesystems](http://www.debian-administration.org/article/Resizing_Encrypted_Filesystems) ) and the ext4 filesystem inside it ( see [http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/ext4grow.html](http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/ext4grow.html) ).

So what is the advantage of LVM? Do I need it?

From this post I get an idea: [https://bbs.archlinux.org/viewtopic.php?id=126502](https://bbs.archlinux.org/viewtopic.php?id=126502)
The guy says he wants to have only one password. Is this one possible reason?

---

### Post by alfonso78 on 2011-10-15
Sorry to reply to myself, but I found this article:
[https://wiki.archlinux.org/index.php/Software_RAID_and_LVM#Introduction](https://wiki.archlinux.org/index.php/Software_RAID_and_LVM#Introduction)

Again, it seems the purpose of LVM is pooling two devices (in this case, RAID devices) together and create various devices on top of it. In this configuration the use of LVM makes total sense.

And finally here I found the final answer!!! :)
[http://stackoverflow.com/questions/237434/raid-verses-lvm](http://stackoverflow.com/questions/237434/raid-verses-lvm)

This is also useful:
[http://serverfault.com/questions/217666/what-is-better-lvm-on-raid-or-raid-on-lvm](http://serverfault.com/questions/217666/what-is-better-lvm-on-raid-or-raid-on-lvm)

---

