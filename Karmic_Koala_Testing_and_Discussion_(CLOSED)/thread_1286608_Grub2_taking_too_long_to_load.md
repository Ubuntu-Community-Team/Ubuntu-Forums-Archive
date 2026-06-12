---
title: "Grub2 taking too long to load"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by lovinglinux on 2009-10-09
I have installed Karmic, keeping the home partition intact. It didn't work well, because something in my old settings where causing a high CPU usage, not detected by top. So I did a fresh install, completely wiping the home settings files and the problem was solved.

But this time, grub2 started to behave badly. It was taking 23 seconds to load every time. The first installation didn't suffer from this problem. I don't know what could be causing this. The only thing I did different was a redistribution of disk space and the creation of some additional partitions.

Anyway, I have solved this problem by installing Jaunty on another partition and thus replacing the grub with the old version. So I can't perform any tests, but I would like to know if someone else is experiencing this or if this has already been reported.

I currently have a triple-boot setup, with Karmic, Jaunty and Windows 7 RC, but when the problem appeared it was a dual-boot with Windows and there was an unused partition where I have installed Jaunty.

---

### Post by ikisham on 2009-10-09
From what I read grub2 is taking more time to boot in general. I'm one case, but it's not too much and I reckon it's in plain development.

---

### Post by mmcmonster on 2009-10-09
From what I understand, Grub2 takes a lot longer when there are more partitions.  Something to do with the way partitions are identified, since it's not the simple /dev/sda1, sda2, etc.

You can google around, but it's a known bug that they are trying to work out prior to release.

There is a workaround, where you edit the grub2 configuration files and replace the unique identifiers with the actual partitions, but I don't know if that gets nuked every time grub gets regenerated (pretty often the last couple weeks).

---

### Post by lovinglinux on 2009-10-09
> **mmcmonster said:**
> From what I understand, Grub2 takes a lot longer when there are more partitions.  Something to do with the way partitions are identified, since it's not the simple /dev/sda1, sda2, etc.

You can google around, but it's a known bug that they are trying to work out prior to release.

There is a workaround, where you edit the grub2 configuration files and replace the unique identifiers with the actual partitions, but I don't know if that gets nuked every time grub gets regenerated (pretty often the last couple weeks).

Thanks for the info. I will wait for the final release to reinstall it.

---

### Post by autocrosser on 2009-10-09
Here is the bug report: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)
 Take a look at it & see if it is what you were having problems with.....

---

### Post by lovinglinux on 2009-10-09
> **autocrosser said:**
> Here is the bug report: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)
 Take a look at it & see if it is what you were having problems with.....

Thanks. Looks like is the same issue, although mine doesn't take minutes to load, but exactly 23 seconds each time.

---

### Post by lovinglinux on 2009-10-11
I have just installed another instance of Karmic on separate disk. The grub from the new installation took over the old one and it is incredibly fast now. I don't know how to explain.

[COLOR="Red"]**Update:**[/COLOR] I was doing some stuff with a Karmic Kubuntu LiveCD, then when I restarted I was lock out completely. Grub loaded fast, but then stalled before the gdm. I had to install Jaunty again in the spare partition to make the old grub take over again. Now I'm back.

---

### Post by VMC on 2009-10-11
> **lovinglinux said:**
> I have just installed another instance of Karmic on separate disk. The grub from the new installation took over the old one and it is incredibly fast now. I don't know how to explain.

[COLOR="Red"]**Update:**[/COLOR] I was doing some stuff with a Karmic Kubuntu LiveCD, then when I restarted I was lock out completely. Grub loaded fast, but then stalled before the gdm. I had to install Jaunty again in the spare partition to make the old grub take over again. Now I'm back.

Maybe had you just re-installed grub2 from original karmic through chroot, that would have solved your dilemma. I guess its too late now to test it out.

---

### Post by lovinglinux on 2009-10-11
> **VMC said:**
> Maybe had you just re-installed grub2 from original karmic through chroot, that would have solved your dilemma. I guess its too late now to test it out.

The other installation was just a test install anyway, so was faster to just reinstall than search for a solution :) Besides, I guess I will stick with the old one until this problem is fixed. Thanks anyway.

---

### Post by lovinglinux on 2009-10-13
> **lovinglinux said:**
> [COLOR="Red"]**Update:**[/COLOR] I was doing some stuff with a Karmic Kubuntu LiveCD, then when I restarted I was lock out completely. Grub loaded fast, but then stalled before the gdm. I had to install Jaunty again in the spare partition to make the old grub take over again. Now I'm back.

This is another issue, not related to the grub problem, but related to nvidia 185 driver. See bug report at [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/421442](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/421442)

---

