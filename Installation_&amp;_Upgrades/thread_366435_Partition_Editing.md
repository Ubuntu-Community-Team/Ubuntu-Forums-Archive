---
title: "Partition Editing"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by bobshowrocks on 2007-02-20
How would I go about making my Ubuntu Partition larger? Specificaly I want to take the disk space from my Windows Partition and add it onto my Ubuntu Partition. Although I would prefer to have the ability to boot into both afterward.

Is it just as easy as using the Live CD?

---

### Post by 23meg on 2007-02-20
You can use Gparted to do it with a graphical interface; the same one in the installer.

---

### Post by bobshowrocks on 2007-02-20
Thanks, I wasn't sure if that could add onto partitions.

---

### Post by bobshowrocks on 2007-02-21
gparted isn't allowing me to expand the partition with Ubuntu on it. Its displaying the Windows partiton, a large unpartitioned space and then the Ubuntu partition. What am I missing here?

---

### Post by dcstar on 2007-02-21
> **bobshowrocks said:**
> gparted isn't allowing me to expand the partition with Ubuntu on it. Its displaying the Windows partiton, a large unpartitioned space and then the Ubuntu partition. What am I missing here?

The partition has to be unmounted, boot off the Live CD (or a Linux Utility CD) and then you should be able to do it.

---

### Post by bobshowrocks on 2007-02-21
Thats what I tryed, it seems to be the GUI thats limiting me. The slider only goes to the right, but the Ubuntu Partition is on the right more side of the picture.

---

### Post by bobshowrocks on 2007-02-22
Are there any other programs that might be able to do this? Able to add onto an partition that is already there?

---

### Post by bobshowrocks on 2007-02-23
Maybe a picture will help.

[IMG]http://lh3.google.com/image/bobshowrocks/Rd54LLe45MI/AAAAAAAAADA/9rugvx5qEfk/Scareenshot1.jpeg?imgmax=1024[/IMG]

This is what the GUI looks like, It wont allow me to extend the ext3 partiton any more. I can make a new partiton, but I don't know how to automaticaly mount it or make it read and writable. What can I do to make my ext3 partition larger?

---

### Post by Herman on 2007-02-23
Hello bobshowrocks,
 Download and burn yourself a copy of [GParted -- LiveCD.]("http://gparted.sourceforge.net/livecd.php") They are free and only a small download and have added capabilities that the Ubuntu version of GParted might not have yet, especially the ability to resize Linux partitions to the left. It's a much slower process but it will work.

There is a way to do it with Ubuntu's GParted but it's complicated to explain. You shrink the partitions and copy and paste the Ubuntu one twice until it's in the place you want it and has the same partition number back, basically. 
When you copy and paste it the first time it will be allocated a different partition number and that can mean you have to perform extra steps to boot it, edit menu.lst and set up /etc/fstab. 
Instead of doing that if you paste the copied of the partition somewhere out of the way, (where you don't want it), delete the original copy of the partition, and then paste it back again, the third copy will be given the original partition number. Then you will be able to boot it right up and not need to edit anything. But that's a little complicated.

If you use GParted LiveCD it will be simple, just shrink your Windows partition and enlarge your Ubuntu partition, not complicated at all.

Regards, Herman :)

---

### Post by donkey42 on 2007-02-23
to resize an existing partition, it would depend on how you did the install to begin with (if you want to boot the install) if the root partition is also the boot partition then you will need to reinstall GRUB, but if you root partition that is a separate from the boot partition (mounted as /boot)

---

### Post by Herman on 2007-02-23
Yes, that's right, resizing doesn't make you have to re-install grub though. Changing the partition number will, if you copy the partition and paste it one time only and get a different partition number. But as long as whatever you do manages to preserve your partition numbering or get back the same partition numbering in the end then you don't have to re-install grub.

It does no harm to re-install grub anyway though if you want to.

Regards, Herman

---

