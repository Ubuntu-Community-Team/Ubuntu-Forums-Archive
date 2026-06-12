---
title: "mounting issue with second NTFS hard drive."
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by bdebruler on 2010-06-28
I installed Ubuntu (Lucid) as a dual boot to my XP home over a month ago and everything seems to be working well with one exception. My second hard drive which is NTFS formatted mounts, but Ubuntu can't remember where recently accessed documents are if they were on that drive.

For instance, I was working on a resume cover letter, saved my work and powered down. When I rebooted, started open office, and tried to access it under the recently used documents, it couldn't find it. There was no problem if I went through the file browser to find it though. Similarly, all my music is on this drive, and will not stay in the rhythmbox library between reboots.

There is no issue accessing the windows partition of the first hard drive (same physical drive as the Ubuntu partitions). During the install I did not try to select a mounting point for the second drive, since I didn't know what would make the most sense (linux noob) and didn't want to risk any data on it. If I remember correctly the guide I followed wasn't clear on what to do with other hard disks (mount as /?????).

So what can I do now to make this second NTFS drive have a consistent mounting point?

---

### Post by darkod on 2010-06-28
There is one important moment. Is the ntfs disk/partition auto mounted on boot or not?

If it isn't, the first time you try to open it from Places it gets mounted, and maybe that's why everything is working once you try to access it manually.

If you want it to be available automatically without needing to open it from Places first, it has to be auto mounted at boot.

If you look in /etc/fstab, for example with:

cat /etc/fstab

does it show there? That's where all devices mounted at boot are. DO NOT change anything right now, just look if it's there.

---

### Post by bdebruler on 2010-06-28
No, it does not show up in  /etc/fstab.

---

### Post by bdebruler on 2010-06-28
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=a770e5c3-fae2-43ef-b65b-a300235e51c5 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=fa5623f6-252c-4ef4-b35f-7fc77571487c /home           ext3    defaults        0       2
# /windows was on /dev/sda1 during installation
UUID=BED03207D031C705 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=df578fff-4058-4cd3-be3b-6c32d1f11161 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by darkod on 2010-06-28
I'm not too experienced with manually editing fstab, so hopefully someone else will jump in too.
In short, you need to create the mount point (folder) first:

sudo mkdir /media/nameasyouwish

Then open fstab with:

gksudo gedit /etc/fstab

and add a line at the end:

/dev/sdb1 /media/nameasyouwish ntfs-3g defaults 0 0

In the above example I assume /dev/sdb1 is the ntfs partition you want to mount. Use the appropriate device name if different. Save and close the fstab file.

PS. More on fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

After restarting that should mount /dev/sdb1 at /media/nameasyouwish on every boot, and the mount point will be the same always.

---

### Post by bdebruler on 2010-06-28
Thanks!

I'll have to read a bit more on editing fstab before I go for it.

Do I have to mount the drive under /media or are there other options?

---

### Post by oldfred on 2010-06-28
+1 on Darko's info

I prefer to directly mount my shared into /home

mkdir /home/fred/shared

fstab entry:
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults                             0  0  

After any editing of fstab run this, if it just comes back it has run ok and remounted everything in fstab or it will give errors. Some error may prevent booting so you should always check.

sudo mount -a

---

