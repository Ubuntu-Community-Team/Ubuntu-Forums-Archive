---
title: "FSCK On Boot"
date: 2010-03-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Coder543 on 2010-03-14
EVERY time I boot my Acer Aspire One (160gb HDD) into Ubuntu Lucid, it does a filesystem check. And it takes **32 SECONDS!** That's just for the fsck. Once it gets past that, it boots in 25-28 seconds, which is amazing. But... why is it doing an FSCK Every. Single. Boot. I don't mind the occasional one, but this is getting ridiculous.

---

### Post by erorrs on 2010-03-14
i think the programme file system check is running every time on the boot.so you should disable it or i think there is a problem in your file system,is your file system is NTFS?If not then change it...

---

### Post by nanog on 2010-03-14
```
sudo tune2fs -c 0 <dev>
```

And before your run this you should at the very least issue:

```
info tune2fs
```

Your RTC (real time clock) could be messed up. This can occur during development or due to hardware failure.

This command should let you know whether there is a problem with the RTC:


```
sudo tune2fs -l <dev> | grep Check 
```

Default check interval should be:
> Check interval:           15552000 (6 months)

You could have an unfixable disk error. Does fsck complete without any warnings? If not, I would strongly recommend running verbose fsck off a chroot (see my sig for linked how to): 

```
sudo fsck -V -r <dev>
```

---

### Post by rondackcpu on 2010-03-14
I have exactly the same problem.  I even tried setting "tune2fs" max count to some relatively big number.  Still fsck on every boot.  There are no "Windows" file systems on the computer.  Only /dev/sda1 as /; /dev/sda2 as swap; and /dev/sda3 as /home.

Any comments would be appreciated.

CRS

---

### Post by Simage on 2010-03-14
I'm having the same concern with my computer running Karmic at the moment, the output from tune2fs is below.

```
tune2fs 1.41.9 (22-Aug-2009)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          0af46d88-fd2c-4ee5-876a-e55b4f88acdd
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      filetype sparse_super large_file
Default mount options:    (none)
Filesystem state:         not clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              5128192
Block count:              10239429
Reserved block count:     511971
Free blocks:              2818930
Free inodes:              4624297
First block:              0
Block size:               4096
Fragment size:            4096
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16384
Inode blocks per group:   512
Last mount time:          Sun Mar 14 06:05:30 2010
Last write time:          Sun Mar 14 13:49:18 2010
Mount count:              2
Maximum mount count:      30
Last checked:             Sun Mar 14 06:01:55 2010
Check interval:           0 (<none>)
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          128

```

Is there any way to determine WHY FSCK is running on boot? i it because the file system is marked not clean, or the max mount count has been exceeded or some other reason??

---

### Post by grandtoubab on 2010-03-14
For me Fsck is not running on each boot, but when it is launched, it never go further than 71 % and the then the boot process continue.
is it because the display is not as fast as the fsck run?
Anyway with system -> administration -> disk tool I see the disk is healthy

---

### Post by Rob2687 on 2010-03-14
I see the fsck message too but I thought it was just some random boot messages between grub and plymouth loading. It didn't occur to me that it might be running and fsck everytime.

Now that I've seen this thread I realized that it sits at the blinky cursor for longer than it shows the plymouth screen. I have always assumed that was because of the slow grub loading...

So basically I am getting the same thing as the OP. After the POST screen I see a blinky cursor for quite a while then the fsck message. After that the plymouth screen for like a split second then GDM. 

Disk utility shows a perfectly healthy hard drive.

---

### Post by sparker256 on 2010-03-14
> **Rob2687 said:**
> I see the fsck message too but I thought it was just some random boot messages between grub and plymouth loading. It didn't occur to me that it might be running and fsck everytime.

Now that I've seen this thread I realized that it sits at the blinky cursor for longer than it shows the plymouth screen. I have always assumed that was because of the slow grub loading...

So basically I am getting the same thing as the OP. After the POST screen I see a blinky cursor for quite a while then the fsck message. After that the plymouth screen for like a split second then GDM. 

Disk utility shows a perfectly healthy hard drive.

I am seeing the same thing. Is there a bug against this?

Bill

---

### Post by Coder543 on 2010-03-14
> **nanog said:**
> ```
sudo tune2fs -c 0 <dev>
```

And before your run this you should at the very least issue:

```
info tune2fs
```

Your RTC (real time clock) could be messed up. This can occur during development or due to hardware failure.

This command should let you know whether there is a problem with the RTC:


```
sudo tune2fs -l <dev> | grep Check 
```

Default check interval should be:


You could have an unfixable disk error. Does fsck complete without any warnings? If not, I would strongly recommend running verbose fsck off a chroot (see my sig for linked how to): 

```
sudo fsck -V -r <dev>
```

I checked and it was set to a 6 month interval. So, i ran the tune2fs -c 0 command and it returned successful. However, rebooting showed a good ol' FSCK. Hmm... my boot time demonstrations would be more impressive to friends if there were no fsck on boot.

---

