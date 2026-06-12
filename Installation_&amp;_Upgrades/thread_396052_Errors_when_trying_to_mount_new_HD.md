---
title: "Errors when trying to mount new HD"
date: 2007-03-29
forum: Installation &amp; Upgrades
---

### Post by KunoNoOni on 2007-03-29
I have a 160gb hard drive that I wanted to add to my server. I did some research and found a guide on adding a new hard drive. here are the steps I did:

[LIST=1]
[*]ran fdisk
[*]chose n to make a new partition
[*]chose p to make it a primary
[*]chose p to print the partition table, /dev/hdc1 was there type was Linux
[*]next I ran mkfs.ext3 /dev/hdc1
[*]I then added it to my /etc/fstab
[*]ran mount -a to mount new hard drive
[/LIST]

thats when I got this error "***mount: wrong fs type, bad option, bad superblock on /dev/hdc1, missing codepage or other error In some cases useful info is found in syslog - try dmesg | tail  or so***"

here is what my fstab looks like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=95f315fd-1a59-4fdc-8ca5-9628ed77ddb2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=7EB4-FC7A  /media/hdb5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb6
UUID=BE7D-D147  /media/hdb6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb7
UUID=FE46-A618  /media/hdb7     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=9dcedfd9-0363-4eb6-b431-51340590c6bc none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
# /dev/hdc1 ***here is the line I added***
/dev/hdc1        /var/www/htdocs/media  ext3    defaults,errors=remount-rw 0    1

the guide I followed is [**here**]("http://wiki.linuxquestions.org/wiki/Adding_Another_Hard_Drive")

oh typing dmesg | tail doesn't show me any errors with the mount. just a bunch of info on eth0

hmmm... does the UUID have anything to do with this? not sure what UUID is though... if so how would I go about getting a UUID for the new drive?

---

### Post by lloyd_b on 2007-03-29
First, you do not need a UUID to mount the partition - that's just a convenience to support newer kernels (though not having a UUID may pose problems if/when you upgrade).

A couple of notes on your fstab entry:
```
/dev/hdc1 /var/www/htdocs/media ext3 defaults,errors=remount-rw 0 1
```

Try this instead:
```
/dev/hdc1 /var/www/htdocs/media ext3 defaults 0 2
```
IIRC, the "errors=remount-rw" only applies to the root filesystem (which must be mounted initially before the normal fsck stage).  

The "pass" setting determines the order in which partitions are run through fsck at boot.  From the "fstab" man page:
> The sixth field, (fs_passno), is used by the fsck program to  deter&#8208;
mine the order in which filesystem checks are done at reboot time.  The
root filesystem should be specified with a fs_passno of  1,  and  other
filesystems  should  have a fs_passno of 2.

I don't know if these issues are the cause of that error, but try changing the fstab and seeing if it makes a difference.

Lloyd B.

---

### Post by KunoNoOni on 2007-03-29
Thanks for the help LLoyd!! It worked :)

---

### Post by crazypiglady on 2008-03-02
Thanks Lloyd. I know this is nearly a year later but thought I'd just say thanks for this information. I followed the same path to the same brick wall as Kuno. Problem solved, Cheers.

---

