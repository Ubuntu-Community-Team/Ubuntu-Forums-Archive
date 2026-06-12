---
title: "Ran out of space on BOOT, can't resize, all space used. help!"
date: 2015-03-01
forum: Installation &amp; Upgrades
---

### Post by jason63 on 2015-03-01
Hey guys. I've had my very first ubuntu server up and running now for about 6 months. Not having any issues.

Specs;
Intel i5
asus h87 mb 
16gb ram
3x WD 4tb reds (mdadm raid5 for backup)
3x WD 2tb greens (mdadm raid5 for media)
1x Maxtor 160GB (os)

Ran into a problem today. While trying to do the package updates through webmin, it kept failing. I dug into it and it turns out im out of space on my boot drive.

Heres a screen shot from gparted live.
[URL="http://ubuntuforums.org/attachment.php?attachmentid=260377&stc=1&d=1425267871My"]http://ubuntuforums.org/attachment.php?attachmentid=260377&stc=1&d=1425267871

[/URL]My OS drive is /dev/sdg

partitions;

/dev/sdg1     -     boot/efi
/dev/sdg2     -     boot  (this is whats filled to max)
/dev/sdg3     -     lvm (contains a 15gb swap logical partition)

I need to expand sdg2 using space contained at the front of sdg3. Gparted live doesnt allow this as it thinks all of sdg3 is allocated. Where do I go from here? I dont know why ubuntu didn't allocate (or moreover why _I_ didnt allocate) more space for boot. This was/is my first ubuntu install.

Thanks for the help guys!

Jason

---

### Post by tgalati4 on 2015-03-01
You probably have several old kernels in /boot.  Keep the latest two and delete the rest.  There are some scripts to do that safely, but you can just delete manually, since you have run out of space and that's generally bad.

According to this thread, they are supposed to be auto-removed.  [http://ubuntuforums.org/showthread.php?t=2239953&highlight=script+delete+kernels](http://ubuntuforums.org/showthread.php?t=2239953&highlight=script+delete+kernels)

Try this:

```
sudo apt-get autoremove
```

Then check for free space:

```
df -h
```

Check your log files (in /var/log) because your LVM partition of 148 GB is also full, and that is bad.

---

### Post by jason63 on 2015-03-01
should that sdg2 partition not be bigger than 244 megs ?

---

### Post by oldfred on 2015-03-01
Gparted will show LVM physical partition as full. But it is just full of the logical partitions inside which should not be full.

While 244MB for /boot is not generous, it is plenty of room for two kernels. You just need to houseclean regularly.

       Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
# kernels, shows older also?
dpkg --list | grep linux-image
sudo apt-get -s autoremove

And/Or:

 In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by jason63 on 2015-03-01
and if i happened to delete the /boot and lvm partitions in an attempt to resize.... full reinstall or can it be saved? I cant see the entire server being stored on /sdg1

---

### Post by oldfred on 2015-03-02
That is what LVM is everything in one partition with only one other small partition for /boot.
See links above on what LVM is.

---

