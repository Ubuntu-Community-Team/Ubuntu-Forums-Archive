---
title: "Karmic slow boot time with ext4"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ingegnerlillo on 2009-10-04
Hi everybody,
I've upgraded two days ago from a very young installation of juanty to karmic, with / mounted on an ext4 partition, and boot become very very slow.

It grows up from 21 second in juanty to 1:17 in karmic.

Some ideas? Here are two bootchart logs...

Thanks in advance and sorry for my horrible english :D

---

### Post by rlieving on 2009-10-04
I just upgraded today and am seeing a similar slow bootup time.  What happened?

---

### Post by tuxxy on 2009-10-04
Maybe you have some errors at boot which are adding the increase in time, what messages do you receive on boot-up? remember Karmic is still beta software.

---

### Post by ingegnerlillo on 2009-10-05
I've tried to boot without quiet and splash options, but I haven't seen any errors...

It seems to hang some seconds before fsck...

Are there some log that I can post to help finding a solution?

Thanks you

---

### Post by moster on 2009-10-05
I too have slow boot and some errors reporting on ext4 partition. I delete it right away and I will NEVER try it again.

---

### Post by ingegnerlillo on 2009-10-05
> **moster said:**
> I too have slow boot and some errors reporting on ext4 partition. I delete it right away and I will NEVER try it again.

It's strange that my ext4 boot partition works very well with Juanty, with a boot time of 21 seconds...

---

### Post by moster on 2009-10-06
> **ingegnerlillo said:**
> It's strange that my ext4 boot partition works very well with Juanty, with a boot time of 21 seconds...

Yes, mine too. But in karmic I think fschk is running in every boot and that is cause of slow boot. I remove karmic because some reports of corrupted data in boot proces and I know there is 100% clean. Maybe new beta grub is cause... who would know.

---

### Post by ingegnerlillo on 2009-10-06
> **moster said:**
> Yes, mine too. But in karmic I think fschk is running in every boot and that is cause of slow boot. I remove karmic because some reports of corrupted data in boot proces and I know there is 100% clean. Maybe new beta grub is cause... who would know.

If you are talking about grub2, I don't think so, because I'm still using the old, good grub :D

Is there a way to make karmic not execute fsck every boot?

I've tried to modify fstab but no success :(

---

### Post by moster on 2009-10-06
> **ingegnerlillo said:**
> Is there a way to make karmic not execute fsck every boot?
I do not know. I was too afraid for my data to continue :D

---

### Post by a6jarvi on 2009-10-06
In Karmic, Bootchart does not stop anymore once the desktop is shown. Instead, it continues to log boot activity until everything is loaded, hence the radical time difference between Karmic's and former bootcharts. For example, on my computer 9.04 booted in 11 seconds according to bootchart, now in 9.10 bootchart shows that the time is 1 min 15 s. 

Too bad I newer measured the full boot times with stopwatch, but Karmic is definitely not that much slower to boot, bootchart is only showing different time. Sure, there are lots of processes that take multiple times longer in Karmic vs. Jaunty, for example when fsck checks wheteher it has to check the disks. I also have a NTFS partition mounted on my computer, and Karmic's fsck doesn't even support NTFS scan yet! So, hoping that everything will be sorted out until they roll out the final version :)

EDIT: ingegnerlillo, if you compare the boootcharts, you see that in 9.04 xorg started at 18s, and in 9.10 it started at 25s. So, if I've understood correctly, 9.10 boots "only" 7 s slower ;)

---

### Post by omegamormegil on 2009-10-09
My Karmic takes a rediculously long time to boot now.  In August booting was pretty quick, but it's gotten quite slow.  I'm still trying to decipher my boot chart.

---

### Post by starzinger on 2009-10-09
> **ingegnerlillo said:**
> If you are talking about grub2, I don't think so, because I'm still using the old, good grub :D

Is there a way to make karmic not execute fsck every boot?

I've tried to modify fstab but no success :(

Check your fstab, it might look like this:


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda4 during installation
UUID=843860bf-81e2-4226-a736-26f00e8cac14 /               ext4    errors=remount-ro 0       1


If you change that last "1" on the line to a "0" (without the quotes), it will not do an fsck every boot. That should improve your boottime, and ext4 should still tell fsck to check it if it's corrupted.

---

### Post by RJARRRPCGP on 2009-10-23
I have the same problem, it boots slowly like Vista does on some systems, but fine when the boot is completed.

And it seems that GRUB takes a long time to even bring up the kernel, like a hard disk drive ready to die! :evil:

---

### Post by zefew on 2009-10-24
> **omegamormegil said:**
> My Karmic takes a rediculously long time to boot now.  In August booting was pretty quick, but it's gotten quite slow.  I'm still trying to decipher my boot chart.

Mine (Karmic) boots in 15 seconds. 

To debug your system, you can follow the procedure below:

1. Edit /etc/default/grub and make the following change:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
&#8594; GRUB_CMDLINE_LINUX_DEFAULT=""

2. Run
$ sudo update-grub

3. Reboot and see where your computer gets stuck.

---

