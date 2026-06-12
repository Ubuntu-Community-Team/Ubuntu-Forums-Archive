---
title: "[SOLVED] Remounting a Previous /home partition as /home in a Fresh Install"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by morning_napalm on 2008-03-05
I just Reinstalled Gutsy and am trying to figure out how to get my /home back.  Here are the details:

1)  I had Gutsy installed with a separate /home partition.
2)  I Did a fresh install of Gutsy, and selected the previous root partition for /, the previous swap partition as swap, and did nothing with the /home partition.

Everything went fine except now I have a new /home on my / partition (sda1) and I have a separate drive sda2 that has all of my old /home information on it.

How do I set sda2 as my /home?

What should I have done differently to avoid this?

Thanks

Here is the contents of my /etc/fstab.  It seems like I need to change something here and do some mounting & unmounting.  I'm just not sure what.

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=9ba5356a-6fa0-46a8-a6f8-b684462bec88 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=B85C9CFD5C9CB798 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb2
UUID=8ce02c3c-46d8-470a-a30f-a27e1671c1fc /media/sdb2     ext3    defaults        0       2
# /dev/sdb3
UUID=77c991c6-5408-45e0-8973-bc1afc9c022c none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


---

### Post by logos34 on 2008-03-06
Basically you needed to specify that it use the existing /home on sda2 but **not** check the '**format**' box. (see 'Clean install' [here]("https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion?highlight=%28upgrade%29"))

You might want to try it again.

---

### Post by morning_napalm on 2008-03-06
Thanks for the help.  I did modify my fstab as shown below and that seemed to work.  Essentially i added the line here to the end of the file:

/dev/sdb2       /home		ext3	defaults	0	2

I'm not sure what happens to the new /home that was created on the install though and sdb2 shows up on my desktop as a drive (I am assuming due to the /media/sdb2 line in fstab).  I will probably reinstall again tonight following the "Clean Install" instructions you referenced.  I had searched all over for that last bit of detail, but couldn't find it.

Thanks again!

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=9ba5356a-6fa0-46a8-a6f8-b684462bec88 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=B85C9CFD5C9CB798 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb2
UUID=8ce02c3c-46d8-470a-a30f-a27e1671c1fc /media/sdb2     ext3    defaults        0       2
# /dev/sdb3
UUID=77c991c6-5408-45e0-8973-bc1afc9c022c none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdb2       /home		ext3	defaults	0	2


---

### Post by logos34 on 2008-03-06
that's not the way to do it--you didn't comment out the old entry.  The system will try to mount the new /home folder there too.

If you wanted to fix this without reinstalling you could have done this (but frankly it's just as easy to reinstall):

Boot from live cd
[B]
sudo mkdir /media/ubuntu

sudo mount -t ext3 /dev/sdb1 /media/ubuntu

cd /media/ubuntu

sudo mv /home /old_home

sudo mkdir /home[/B]

Edit fstab to add
> /dev/sdb2 /home ext3 defaults 0 2

in place of
> # /dev/sdb2
UUID=8ce02c3c-46d8-470a-a30f-a27e1671c1fc /media/sdb2 ext3 defaults 0 2

---

### Post by morning_napalm on 2008-03-06
Thanks Logos34.  I will probably just reinstall like you said.  It will hopefully end up much cleaner.  I figured I was missing something.:)

---

### Post by morning_napalm on 2008-03-10
Reinstalling and following the directions in the above links worked great.  I just need to reinstall the various software packages I had before.

thanks for the help.  Next time will be much more smooth!

I can now share my printers easily with our other *buntu machine.  I couldn't get them to work before, but with the fresh install on this machine, they were a piece of cake.

Now to figure out file sharing!

:guitar:

---

