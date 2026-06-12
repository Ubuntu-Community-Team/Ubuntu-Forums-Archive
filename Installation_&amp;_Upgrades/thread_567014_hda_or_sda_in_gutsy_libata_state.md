---
title: "hda or sda in gutsy? libata state?"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by plamen_todoroff on 2007-10-04
I have one hdd in my laptop, separated in 20 partitions, 3 primary (win, boot, root) and 1 extended with 17 logical partitions in it. When I first installed Feisty I used Partition Magic 8 to repartition the hdd and form the above mentioned scheme, then I mounted all partitions manually in the feisty graphical installer, installation finished and login successful, and then i found that only the first 15 partitions were available, the last 5 showed up empty in nautilus. I google-d a little to find that this was due to some libata thingy changed in the new kernels and from 2.6.19 all hda drives were to be handled as sda thus limited to 15 partitons. I played with fglrx, xgl, c-fusion a little and messed it all up so i decided to go for a clean reinstall, i put the exactly same dvd again and did the exactly same things during installation, and when i logged in all 20 partitions where mounted and my files were nicely showing in nautilus. So the question is wtf could have been different in my reinstall, and, if from now on all hda will be treated as sda does this mean that i won't be able to use my 20 partitions in gutsy? It's really important to me. I've never expected to be so much attracted be linux as to not want to go back to windows anymore, but it happened and i need some help to stay in the free world. Every answer is appreciated. So, hda or sda in Gutsy?
P.S. For all those asking (please don`t make this the main point of this thread) why the hell i need so many partitions: If I had separate partitions for /, /boot, /usr, /home and /var, installing 3 distros and a swap file exceeds the limit of 15, doesn't it?

---

### Post by dabl on 2007-10-04
You asked for help ....  here's the best I got.  :lolflag:

For desktop/workstation use, unless you need one of the exotic filesystems (xfs, jfs, etc.), you really only want 3 partitions for Linux:

/
/home
swap

If it's important to have a shared NTFS data partition, then add /NTFSDATA to your /etc/fstab table after you have a successful installation up and running with the 3 listed above.

So, Help #1 is -- you're overdoing the complexity of your installation and getting bit by it.  You can share the swap with any other Linux, but I don't recommend sharing any of the other partitions -- /home, for example, has desktop settings and autostart programs in it, and will get messed up by the "most recent Linux" that used it, if you try to share it.

hda vs. sda vs. libata driver vs. ata.piix -- IMHO, there's been an exaggerated over-reaction to the simple need to change the Linux device-identifying architecture to accommodate the proliferation of USB and SATA devices.  It seems that everyone who was so comfortable with the /dev/hdn system has a dent in his karma, but the reality is it doesn't handle the USB bus worth a %&*@, so they fixed it with the UUID system.  Why PATA/IDE drives needed to be dumped into the /dev/sdn device nomenclature I have no idea, but it doesn't really matter for any practical purpose.  Just set up your /etc/fstab table using UUID numbers, and you'll be fine.  For USB drives (thumb or external), use ```
fdisk -l
``` or ```
hwinfo
``` to determine their /dev/disk/by-id number, and use the UUID number that you get from ```
blkid
``` and it will be fine.

Help #2:  do /etc/fstab like this (FYI, sda is an old IDE drive and the others are SATA drives, with a NTFS-formatted USB thumb drive at the end):

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sdb1
UUID=b1869c3e-b13a-4772-914c-bcc6db718967 / reiserfs nouser,notail,noatime,auto,rw,dev,exec,suid 0 1
# /dev/sdb2
UUID=a6c2ba7b-8492-4746-92af-5182dcb4daab /home reiserfs nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2
# /dev/sda1
UUID=f222f97f-278f-4db5-8642-513294f30193 /media/sda1 reiserfs nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2
# /dev/sda3
UUID=adf641ca-f64e-4311-bc30-86bfcdcb669c /media/sda3 reiserfs nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2
# /dev/sdc1
UUID=1ddd0144-0875-4667-9f98-e90a23f58ff3 /media/sdc1 reiserfs nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2
# /dev/sdc2
UUID=710efad8-9f97-4bcd-8f57-8f8cc1facc2f /media/sdc2 reiserfs nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2
# /dev/sdc3
UUID=f1912a56-2e5c-45ce-b91b-3ebbe69e20f4 /media/sdc3 reiserfs nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2
# /dev/sdd1
UUID=cffddf89-57f3-40ab-a97f-40bb1ea45f16 /media/sdd1 reiserfs nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2
# /dev/sdd3
UUID=9b7658da-59e1-4b2b-a4b9-fa3ee11b68cf /media/sdd3 reiserfs nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2
# /dev/sde1
UUID=d182b7c3-298c-49b3-ac66-b378033b815c /media/sde1 reiserfs nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2
# /dev/sdd2
UUID=94d4d572-3581-491b-90dc-e5f619c65908 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
# /dev/sdf1
UUID=A8FC3435FC33FC5E /media/NTFSTICK ntfs-3g user,atime,rw,nodev,nosuid 0 0
```

fglrx -- I fixed my ATI problem with my wallet and bought an Nvidia card .....  :lolflag:

Good luck with it!  :)

EDIT: Says [[COLOR="Lime"]**here**[/COLOR]](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/install-guide/ch-partitions.html), if you read down far enough, "due to the way partitions are accessed in Linux, you should avoid defining more than 12 logical partitions on a single hard drive".  For whatever that's worth.  So I'm deducing that 4 primary + 12 logical = 16 total is kind of the outer limits of a "smart" partitioning scheme for a single disk.   ;-)

---

