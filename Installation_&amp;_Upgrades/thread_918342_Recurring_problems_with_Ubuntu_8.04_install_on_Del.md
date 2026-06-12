---
title: "Recurring problems with Ubuntu 8.04 install on Dell Vostro 1500"
date: 2008-09-12
forum: Installation &amp; Upgrades
---

### Post by mushroomcloudwarrior on 2008-09-12
Hi, I'm a newbie and have searched the forums unsuccessfully and am writing hoping for answers. 

I had Kubuntu on my laptop which i didn't particularly like, and i couldn't get it to work with the dell vostro 1500 hardware (a lot of threads on here reporting the same)Although i heard good things about the 8.04 working well with this particular laptop.

After reading a thread on here, i deleted the Kubuntu installed partition (through my computer>manage>Disk management) so there was about 9.53 gigs of space free on it, although it was in the middle in case that matters. here's a screenshot:

[IMG]http://i36.photobucket.com/albums/e37/mushroomcloudwarrior/Noname.jpg[/IMG]

I booted with the Ubuntu cd, installed it, and when it asked me about partitions, i selected "select automatically using the longest available partition" which i assumed it would do right. When i tried booting into the newly installed ubuntu, i got the "Kernel Panic - not syncing: vfs: unable to mount root fs on unknown-block" error. This error seems to be pretty common, however, it spits out partition numbers at the end of it, while it's just said "unknown block" in my case. 

I really don't know what's gone wrong, except I think I should assign the partitions myself? (in which case, tell me what would be a healthy partition for 2 gigs of ram). As you've noticed, the 9.53 gigs available was the space kubuntu took. The 80.77 gigs partition is an ext2, being accessed through windows using ext2 reader. 

Is it a GRUB problem? i mean grub not being able to find the right partition. 

I'm willing to read a bit if you can point me in the right direction. However, if it's only one step that i'm missing, please just tell me because i'm very eager to use ubuntu after having no choice and using xp for a long year. 

Thanks

---

### Post by mushroomcloudwarrior on 2008-09-12
For the record, 

I've already done this:

```
sudo mount /dev/sda6 /mnt
sudo chroot /mnt /bin/sh
sudo update-initramfs -u
```

without any luck. I don't exactly remember what the output was, sorry..but it wouldn't accept it on the last command.

Apologies for the bad explanation!

---

### Post by mushroomcloudwarrior on 2008-09-13
bump for help. I'm writing this from the live cd, and can't access xp because i've formatted the linux partition and taken grub with it.

:(

---

