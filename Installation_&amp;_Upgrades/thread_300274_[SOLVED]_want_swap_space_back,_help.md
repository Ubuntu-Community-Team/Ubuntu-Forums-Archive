---
title: "[SOLVED] want swap space back, help"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by rfruth on 2006-11-15
My performance is not quite up to snuff (things are working though) so I got to poking around and found my sway space is no longer in use, how do I reenable it  (/dev/sda5 = swap so partition is there) ?

output of free command
```

rfruth@rfruth-desktop:/etc$ free
             total       used       free     shared    buffers     cached
Mem:        514492     501364      13128          0      56772     240136
-/+ buffers/cache:     204456     310036
Swap:            0          0          0

```

my /fstab file
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=2CA6-0780 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=ab6b125c-9771-40a3-ac63-3659a46fac99 none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0



```

---

### Post by dcstar on 2006-11-15
> **rfruth said:**
> My performance is not quite up to snuff (things are working though) so I got to poking around and found my sway space is no longer in use, how do I reenable it  (/dev/sda5 = swap so partition is there) ?
......
```
man swapon
``` will give you some usable info.

---

### Post by rosieg on 2006-11-16
I found that after upgrading to Edgy my swap space was no longer being mounted. I found this link useful:

[https://launchpad.net/distros/ubuntu/+bug/66637]("https://launchpad.net/distros/ubuntu/+bug/66637")

If you scroll down this page towards the bottom there are step by step instructions for fixing the problem that I had.

---

### Post by rosieg on 2006-11-16
Sorry for just posting the link - here is the relevant bit:


> follow THESE instructions and report back
>
> 1, determine your swap with 'fdisk -l'
[COLOR="Blue"]it is /dev/hda2[/COLOR]

> 2, do mkswap on your swap partition - RECORD THE UUID WHICH THIS COMMAND
> OUTPUTS
[COLOR="Blue"] mkswap /dev/hda2
Setting up swapspace version 1, size = 1496993 kB
no label, UUID=eb19acf3-bf59-484b-beac-a46f6b3dc990[/COLOR]

> 3, now use this UUID to put into fstab and resume
> files...(RESUME=UUID=<the-swap-partition-uuid-from-vol_ID
> should go in /etc/initramfs-tools/conf.d/resume

[COLOR="Blue"]done[/COLOR]

> 4, update-initramfs -u
[COLOR="Blue"]done, without errors
[/COLOR]
> 5, reboot normally after this finishes
[COLOR="Blue"]now it works.
THANKS A LOT.[/COLOR]

The sections in [COLOR="Blue"]blue[/COLOR] are what one user found as they followed the instructions. I found them useful to reassure myself that I was doing the right things. MAke sure you also put the UUID into fstab - I missed this step first time round!

---

### Post by rfruth on 2006-11-16
I'm close but not sure of syntax of the resume file, here is mine, is it correct  (assuming the UUID is ok)  ?

```

RESUME=UUID=8d721728-90e5-46d6-a647-2b97e25f5753

```

---

### Post by rosieg on 2006-11-17
That looks about right :-)

---

### Post by BLTicklemonster on 2007-02-17
??? I have a game I play, and it crashes a good bit. I notice that conky shows my cpu and memory totally used up when the game is running. I have a gig of ddr400 ram, and an amd cp 2600+ processor. So I got to thinking maybe Linux had something that would help me manage my memory. swapspace is in the repositories, I wonder about it? 

Anyway, I found this thread, and entered

fdisk -l

and nothing showed up. it just went back to the basic command line.

My fstab shows my swap space as

/dev/hdd2  none           swap         sw                                  0  0  

whereas 

mkswap /dev/hdd2

gets me this:

Setting up swapspace version 1, size = 2961096 kB
no label, UUID=5e75ef63-3e8d-4119-ae49-662510890e08

So I reckon I ought to use the UUID instead of what's in fstab right now? How do I go about doing this? What steps, what files, etc. I know it ought to go in fstab, but Im not sure exactly what I ought to put. And what is resume file? How do I edit that?

---

