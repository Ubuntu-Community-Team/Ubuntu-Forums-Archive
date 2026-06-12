---
title: "swap file won't mount during install"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by bxdobs on 2008-03-20
The Basic install from iso CD Ubuntu is complaining it cannot mount a file system with type swap in IDE1 Master, Partition #2 (hda2) at None failed.

I suspect this is because the partition hasn't been formatted ... however going into the partition menu the GUI interface won't allow me to check the Format box for the swap partition

The threads surrounding this question seem to be going nowhere is this an issue with my hardware or is there a way forward?:confused::confused:

---

### Post by Pumalite on 2008-03-20
How did you install? Give details. /swap has it's own format.

---

### Post by bxdobs on 2008-03-20
had a 20G laptop AMD K6 kicking around wanted to try out Linux ... loaded RED HAT 9 but it is missing drivers for Reltek 1389 /dlink dfe690txd ... downloaded a c file from dlink but it won't compile ... missing some lib files 

So downloaded ubuntu, burned iso cd, and booted ... using the menu I did the install ... step 4 failed the first attempt so went back manually deleted all partitions and created a root 19000 MB et3 partition format flagged and a 1003 swap partition ... after step 7 the process starts formatting the root partition then halts when attempting to mount the swap patition

---

### Post by Pumalite on 2008-03-20
You might have made a mistake assigning 'mount point' for /swap. It has to be 'swap'

---

### Post by bxdobs on 2008-03-20
The Partitioner doesn't let you set a mount point for a SWAP partition ... I still cannot get past this point with a swap partition so now attempting to install without one (this apparently is the only option given by the installer that I can see)

---

### Post by Pumalite on 2008-03-20
If you go 'Manual', you can create partitions and assign them their mount points.

---

### Post by bxdobs on 2008-03-20
That is where I am attempting to change the partition

I have set /dev/hda1 to mount at / and it is an ext3 type Format 19000
                /dev/hda2                                        swap type              1000

the hda2 partition the moment you select swap type will not allow a mount point (greyed out) or a format (checkbox border greyed out)

---

### Post by Pumalite on 2008-03-20
You could use Gparted Live CD which I prefer for all my installations:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.
Prepare your partitions and then install Ubuntu going Manual and using these partitions.

---

### Post by wolfen69 on 2008-03-20
if you are using the whole drive for ubuntu, there is no need to make swap. choose "use entire disk" (instead of manual) and it will automatically set up swap for you.

---

