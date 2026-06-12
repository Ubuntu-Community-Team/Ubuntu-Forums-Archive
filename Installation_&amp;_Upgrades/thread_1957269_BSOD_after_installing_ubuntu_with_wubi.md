---
title: "BSOD after installing ubuntu with wubi"
date: 2012-04-12
forum: Installation &amp; Upgrades
---

### Post by S3P3HR on 2012-04-12
hello.
i installed ubuntu with wubi.
now i cant access my windows 7 ultimate 64bit it gives bsod.
and the drive D that i installed ubuntu seems to be missing (not showing in ubuntu).
i allocated 17gig to ubuntu and the rest is not there!i had lots of valuable files!are they gone?
one more thing:wubi didnt downloaded anything,just installed.is this because i had iso and wubi in the same directory?
please help me,i want my windows back :(
ubuntu works fine...

---

### Post by darkod on 2012-04-12
Yes, if you have wubi.exe and the ISO in the same folder, it will use the iso and not download anything.

Lets see what you have on the disk. If you can, burn a cd from the iso and boot with it into live mode (Try Ubuntu). Once booted, open Terminal and post the output of:
sudo fdisk -l (small L)

On another note, installing ubuntu as proper dual boot on its own partition is much better than wubi.

---

### Post by S3P3HR on 2012-04-12
> **darkod said:**
> Yes, if you have wubi.exe and the ISO in the same folder, it will use the iso and not download anything.

Lets see what you have on the disk. If you can, burn a cd from the iso and boot with it into live mode (Try Ubuntu). Once booted, open Terminal and post the output of:
sudo fdisk -l (small L)

On another note, installing ubuntu as proper dual boot on its own partition is much better than wubi.
thanks for the reply.
here is the file:
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xddbcb842

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   102402047    51097600    7  HPFS/NTFS/exFAT
/dev/sda3       102402048   759794174   328696063+   7  HPFS/NTFS/exFAT
/dev/sda4       759794175   976768064   108486945    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 4026 MB, 4026531840 bytes
128 heads, 30 sectors/track, 2048 cylinders, total 7864320 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     7864319     3932128+   b  W95 FAT32
sepehr@ubuntu:~$ 

i used wubi 'cause i thought its less difficult than setting up dualboot.
last time i ****** entire mbr setting up dual boot.
i guess it was a mistake,installing ubuntu in the first place.

---

### Post by S3P3HR on 2012-04-12
problem solved
i was at bathroom,and pc automatically entered windows startup repair (i was restarting).
and after 7years of working with windows,startup repair worked for the first time!!
guess its microsoft being microsoft right? :-|

---

### Post by darkod on 2012-04-12
Actually I would say the dual boot is easier because the OSs are separated. Wubi is running inside windows and sometimes when you think the problem is with wubi it turns out windows might be making it.

If you do have win7 dvd or rescue cd, try booting with it and opening a command prompt. After that try running chkdsk.

Or you can try the automated repair process of the win7 disc.

The partitions on the disk look OK as far as their size is concerned. I thought maybe some partitions got overlapped, but that is not the case.

---

### Post by bcbc on 2012-04-12
Wubi doesn't cause BSOD. That's a Windows and/or hardware issue only.

Those 'missing files' that are on D: are there, but mounted as /host

It's funny that Ubuntu boots but not Windows, right? I had the same experience recently, except it was my Windows-only computer (never booted linux on it) that gave a BSOD and promptly died. Boot repair/system restore didn't work. I had to boot a linux CD to reformat the drive before I could reinstall Windows... but it still gives a BSOD. So I installed edubuntu on it - and the thing works fine, just not Windows. :confused:
I suspect the hard drive is failing, but not sure why Linux is immune to this, and not Windows. 
So... long story short... your BSOD is for some other reason.

---

### Post by jadtech on 2012-04-12
BSOD can also be a failing processor or cause by over heating  maybe fans and such need cleaning..kard bell back when use to 

i had an oldpacblue screeen a lot come to find out something was wrong with the video card and it smoke the monitor on boot up one morning flames out the back and all..

come to think of it linux installing has came a long way ovr the last 15 years I remember installing red hat in the early 90 the CD they would send you had a warning to not install the wrong video chip set it could cause you monitor to brust into flames ..

---

