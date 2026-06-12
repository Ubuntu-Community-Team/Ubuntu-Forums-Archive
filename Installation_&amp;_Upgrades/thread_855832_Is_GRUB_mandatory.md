---
title: "Is GRUB mandatory?"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by psycroptik on 2008-07-10
...OR can I just install another boot manager, like Acronis Boot manager?

psycroptik

---

### Post by tamoneya on 2008-07-10
if you prefer acronis that is fine.  GRUB is just the linux standard thats all.

---

### Post by SkonesMickLoud on 2008-07-10
You can use Acronis, but it costs $50.  GRUB and LILO are free.

---

### Post by psycroptik on 2008-07-10
I am setting up Ubuntu on RAID5 and its being such a pain.
Well GRUB that is, the install went well. I found Acronis for 24.99 and if it works then its way better then trying to get GRUB to work.

Thanks guys,
psycroptik

---

### Post by SkonesMickLoud on 2008-07-10
What grub issues are you running into?

---

### Post by sdennie on 2008-07-10
> **psycroptik said:**
> I am setting up Ubuntu on RAID5 and its being such a pain.
Well GRUB that is, the install went well. I found Acronis for 24.99 and if it works then its way better then trying to get GRUB to work.


Switching from grub may not help you in this case.  If you've set the root partition as software RAID5, I'm not sure if any boot loader will help you.  I believe that when I setup a RAID 5 machine, I setup a smallish (5GB) / as RAID1 on each disk and used grub to write the MBR of each disk to make it bootable.  Then I partitioned the rest of the disks as a big RAID5 array.  This means that disk failure doesn't break the boot process and, because the root partition is just mirrored, it can be booted from any disk.

---

### Post by kd5ful on 2008-07-11
> **SkonesMickLoud said:**
> What grub issues are you running into?

I'll bite.

  Error 2.
Someone else suggested going with [color=red][this](http://www.supergrubdisk.org/)[/color] for a possible fix.
  As of presstime here, I am in XP, and am pretty upset at having lost the use of my Ubuntu drive.
...It feels like I just had two of my fingers lopped off my right hand by some strange and vicious monster.
(yes, that was a book reference)
-James

---

### Post by SkonesMickLoud on 2008-07-11
Are you able to boot into the LiveCD?

If so, boot into that, load up GParted (System >> Admin >> Partition Editor) and let me know what the name of the partition containing your Ubuntu install is.  It should be something like sdaX.

---

### Post by kd5ful on 2008-07-11
> **SkonesMickLoud said:**
> Are you able to boot into the LiveCD?

If so, boot into that, load up GParted (System >> Admin >> Partition Editor) and let me know what the name of the partition containing your Ubuntu install is.  It should be something like sdaX.

Allrighty.
Yes, I have an older ver. of Gutsy (7.10, I think), and I can boot it.
I'll do so, but tomorrow sometime.
Unfortunately, my business is driving this truck, and it has to come first.
Thanks.

---

### Post by psycroptik on 2008-07-11
> **SkonesMickLoud said:**
> What grub issues are you running into?

Well.. From Memory since I'm working on something else..

I created the partitions from Acronis, loaded dmraid and went to install Ubuntu. It went fine, saw the partitions, installed etc..

I let it choose the partition to boot from automatically and tried a few other ways also.

I would remove "quiet splash" and the last error I got before it went to busybox was something like...

/dev/mapper/<my_partition_with_root> cant be found.

So I just figured that GRUB cant handle the RAID properly..

---

### Post by sdennie on 2008-07-11
> **psycroptik said:**
> Well.. From Memory since I'm working on something else..

I created the partitions from Acronis, loaded dmraid and went to install Ubuntu. It went fine, saw the partitions, installed etc..

I let it choose the partition to boot from automatically and tried a few other ways also.

I would remove "quiet splash" and the last error I got before it went to busybox was something like...

/dev/mapper/<my_partition_with_root> cant be found.

So I just figured that GRUB cant handle the RAID properly..

See post #6...

---

### Post by psycroptik on 2008-07-11
> **vor said:**
> See post #6...

My MB only allows me to use RAID5/0 at the same time.

---

### Post by SunnyRabbiera on 2008-07-11
Grub is a standard on most distros, though there is lilo though I dont know if you can install it by its lonesome... I know grub has supergrubdisk and projects like it but I dont know about lilo

---

### Post by psycroptik on 2008-07-11
Restarting now, wish me luck ;)
Should of read the documentation, it needs something like grub or lilo installed.

Now Ill never go to sleep..

---

### Post by psycroptik on 2008-07-11
I'm getting there I think... Seems to mount the partition but now I'm getting a ERROR 15 File not found.

Time for sleep, Ill try to fix it in the morning.

---

### Post by VMC on 2008-07-11
> **psycroptik said:**
> I'm getting there I think... Seems to mount the partition but now I'm getting a ERROR 15 File not found.

Time for sleep, Ill try to fix it in the morning.

Grub Error 15, usually means file not found. Like missing your vmlinx file or can't find it.

Here is a good Grub Error discription on all  [Grub ERRORS]("http://www.gentoo.org/doc/en/grub-error-guide.xml")

---

### Post by psycroptik on 2008-07-11
I think a fake RAID5 is a no go for Ubuntu..

device-mapper: table: 254:0: raid45: unknown target type
device-mapper: ioctl: error adding target to table
ERROR: device-mapper target type "raid45" not in kernel

I guess software raid it is ;)
Really not looking forward to breaking these windows arrays and re-imaging. Blast.

---

