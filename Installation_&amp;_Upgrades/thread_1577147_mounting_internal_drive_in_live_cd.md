---
title: "mounting internal drive in live cd"
date: 2010-09-18
forum: Installation &amp; Upgrades
---

### Post by eripey on 2010-09-18
Okay, I was having problems booting from the live cd with a blank screen.

So I did some searching and I needed to put 

i915.modeset=1

after that, my install went fine.  After booting, it was a blank screen again.  So from the search I did, I needed to edit the grub and add

i915.modeset=1

I booted from the live cd and was able to edit the grub, but this is where I am stuck, I get an error running 
sudo update-grub

some error about my /dev being mounted, I did some research and looks like I need to mount my internal hard drive while in live cd.  

So...I looked and searched and couldn't find anything about mounting my internal drive from the live cd to get the update-grub to run.  I read the man pages for mount but nothing useful.

So I think it might be simple for the experts here, How do I mount my internal drive when running in live cd?

---

### Post by gnush on 2010-09-18
```
sudo fdisk -l
```Mount the appropriate drives/partitions using the *mount* command.

[U]Example:
[/U]```
sudo mkdir /mnt/disc
sudo mount /dev/sdaX /mnt/disc
```Change sdaX to the drive and partition you want to mount.

**Edit:**
The X in sdaX should be the partition you wish to choose. For example, sda1 is the first drive and the first partition of that drive.
[http://en.wikipedia.org/wiki/Device_file_system#Naming_conventions](http://en.wikipedia.org/wiki/Device_file_system#Naming_conventions)

---

### Post by eripey on 2010-09-18
Thanks for the quick reply!

Okay, I was able to do the steps, but I still get this error after running 

```

sudo update-grub

```

```

/usr/sbin/grub-prob: error: cannot find a device for / (is /dev mounted?).

```

Have any ideas?

---

### Post by gnush on 2010-09-18
> **eripey said:**
> Have any ideas?


Does it work to add *-v*, *-vv*, and/or *--verbose* after *grub-update*?

Example:
```
sudo update-grub --verbose
```Also, have you tried to google the error message?
[http://www.google.com/cse?cx=013269018370076798483:gg7jrrhpsy4&cof=FORID:1&q=/usr/sbin/grub-prob:+error:+cannot+find+a+device+for+/+%28is+/dev+mounted%3F%29.&sa=Search](http://www.google.com/cse?cx=013269018370076798483:gg7jrrhpsy4&cof=FORID:1&q=/usr/sbin/grub-prob:+error:+cannot+find+a+device+for+/+%28is+/dev+mounted%3F%29.&sa=Search)

---

### Post by eripey on 2010-09-18
verbose just show the version number with no error

> /usr/sbin/grub-mkconfig (GNU GRUB 1.98-1ubuntu7)

---

