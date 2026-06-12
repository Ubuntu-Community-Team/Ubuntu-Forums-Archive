---
title: "Upgrade 15.10 to 16.04 Problem with FSTAB file"
date: 2017-08-10
forum: Installation &amp; Upgrades
---

### Post by mike.lussier on 2017-08-10
Good morning all, 
I have been playing with this on and off for almost a year now. I have a home media server that has 6 external NAS units connected via esata boards. I use NFS to access them accross my internal network. in my fstab file I use the UUID to mount all of the drives. all of my system mounts for NFS and all of my export bindings. 
when I upgraded to 16.04 the system goes into a failsafe. I found the fix was to save my fstab  to fstab.loaded and bring back the original fstab file.

Any thoughts ? 

```


# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=b3431642-bccb-4ac8-b801-7b7eea471a02 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e2eba8eb-c180-4e0f-9cb9-1af4e2a32828 none            swap    sw              0       0
#
# DRIVES
# 1 & 2
UUID=631aa797-3ed2-4203-adc6-920009b714e8 /media/mediaserver/BACKUP-1        ext4        defaults    010
UUID=5b2d40ff-af83-4338-9dce-d24a52aefe1f /media/mediaserver/BACKUP-0        ext4        defaults    011
#3 & 4
UUID=b14bbb96-441c-41ae-87fb-4a4aeae1c8ad /media/mediaserver/ADULT-AREA        ext4        defaults    012
UUID=3387adcb-de5c-4ec1-9da6-10756516d3a7 /media/mediaserver/MOVIES-UPDATE    ext4        defaults    013
# 5 & 6
UUID=eb6fd032-e639-44d9-bc9c-ed0797faf051 /media/mediaserver/MOVIES-01        ext4        defaults    014
UUID=932583b5-04b9-4868-b76c-16f4487a59c9 /media/mediaserver/DOCUMENTS-02    ext4        defaults    015
# 7 & 8
UUID=7650aa37-3cf8-413d-9c15-cf1e978f95e8 /media/mediaserver/SPECIAL        ext4        defaults    016
UUID=1171a069-aa7f-4239-8476-00515462e7ac /media/mediaserver/TVSHOWS-04        ext4        defaults    017
# 9 & 10
UUID=4440a8a3-a069-4b8c-8ede-87e8b0b69e5a /media/mediaserver/SYSTEM-IMAGES-02    ext4        defaults    018
UUID=07c13d2c-6146-464a-ade6-7f2ebfb4b8fd /media/mediaserver/TVSHOWS-MASTER    ext4        defaults    019
# 11 & 12
UUID=5260aa48-e679-4573-92bb-65c79c089dad /media/mediaserver/TVSHOWS-01        ext4        defaults    020
UUID=d2cbe3e9-ae46-4e64-8cb8-a852e1102ba5 /media/mediaserver/MOVIES-00        ext4        defaults    021
# 13 & 14
UUID=5c944401-6f4f-4582-ace0-f98aec4e3fad /media/mediaserver/MUSIC-01        ext4        defaults    022
UUID=f9d3a0e3-78c8-4e49-9ce4-b66b0adccb51 /media/mediaserver/MOVIES-MASTER    ext4        defaults    023
# 15 & 16
UUID=9a5a09a8-9358-464a-8d6c-2e4decea2d5d /media/mediaserver/TVSHOWS-03        ext4        defaults    024
UUID=14d2f3a3-c6f9-4c95-b538-2ecd2bcb7dde /media/mediaserver/DOCUMENTS-03    ext4        defaults    025
# 17 & 18
UUID=60b13284-b9e2-44d9-95be-feb145ae3cc0 /media/mediaserver/MUSIC-00        ext4        defaults    026
UUID=967539ad-e9e2-4407-98fe-7c9def0cf006 /media/mediaserver/TVSHOWS-05        ext4        defaults    027
# 19 & 20
UUID=a52c2de6-cd32-4854-8386-44f04950481b /media/mediaserver/TVSHOWS-02        ext4        defaults    028
UUID=58c0385b-70ee-4d11-813d-5941d984ea8b /media/mediaserver/DOCUMENTS-01    ext4        defaults    029
# 21 & 22
UUID=83bc14d3-7b70-450b-ae40-a9501fe4a497 /media/mediaserver/SYSTEM-IMAGES-01    ext4        defaults    030
UUID=1f3a0b93-f7f9-4aaf-8f7a-c66be69b1312 /media/mediaserver/PICTURES-00    ext4        defaults    031
#
#
#
#
# SYSTEM MOUNTS FOR NFS
#
/media/mediaserver/TVSHOWS-01        /exports/TVSHOWS    none    bind    0    0
/media/mediaserver/MOVIES-00/        /exports/MOVIES        none    bind    0    0
/media/mediaserver/DOCUMENTS-01        /exports/DOCUMENTS    none    bind    0    0
/media/mediaserver/MUSIC-00        /exports/MUSIC        none    bind    0    0
/media/mediaserver/PICTURES-00/        /exports/PICTURES    none    bind    0    0
/media/mediaserver/SYSTEM-IMAGES-01/    /exports/SYSTEMS    none    bind    0    0
#
#
# DRIVE ACCESS
#
#
# Drives for remote access
#
/media/mediaserver/BACKUP-0            /exports/DRIVES/BACKUP-0    none    bind    0       0
/media/mediaserver/BACKUP-1            /exports/DRIVES/BACKUP-1    none    bind    0    0
/media/mediaserver/PICTURES-00            /exports/DRIVES/PICTURES-00    none    bind    0    0
/media/mediaserver/DOCUMENTS-01            /exports/DRIVES/DOCUMENTS-01    none    bind    0    0
/media/mediaserver/DOCUMENTS-02            /exports/DRIVES/DOCUMENTS-02    none    bind    0    0
/media/mediaserver/DOCUMENTS-03            /exports/DRIVES/DOCUMENTS-03    none    bind    0    0
/media/mediaserver/SPECIAL            /exports/DRIVES/SPECIAL        none    bind    0    0
/media/mediaserver/MOVIES-00            /exports/DRIVES/MOVIES-00    none    bind    0    0
/media/mediaserver/MOVIES-01            /exports/DRIVES/MOVIES-01    none    bind    0    0
/media/mediaserver/MUSIC-00            /exports/DRIVES/MUSIC-00    none    bind    0    0
/media/mediaserver/MUSIC-01            /exports/DRIVES/MUSIC-01    none    bind    0    0
/media/mediaserver/TVSHOWS-MASTER        /exports/DRIVES/TVSHOWS-MASTER    none    bind    0    0
/media/mediaserver/TVSHOWS-01            /exports/DRIVES/TVSHOWS-01    none    bind    0    0
/media/mediaserver/TVSHOWS-02            /exports/DRIVES/TVSHOWS-02    none    bind    0    0
/media/mediaserver/TVSHOWS-03            /exports/DRIVES/TVSHOWS-03    none    bind    0    0
/media/mediaserver/TVSHOWS-04            /exports/DRIVES/TVSHOWS-04    none    bind    0    0
/media/mediaserver/TVSHOWS-05            /exports/DRIVES/TVSHOWS-05    none    bind    0    0
/media/mediaserver/MOVIES-MASTER        /exports/DRIVES/MOVIES-MASTER    none    bind    0    0
/media/mediaserver/ADULT-AREA            /exports/DRIVES/ADULT-AREA    none    bind    0    0
/media/mediaserver/MOVIES-UPDATE        /exports/DRIVES/MOVIES-UPDATE    none    bind    0    0
/media/mediaserver/SYSTEM-IMAGES-01        /exports/DRIVES/SYSTEM-IMAGES-01    none    bind    0    0
/media/mediaserver/SYSTEM-IMAGES-02             /exports/DRIVES/SYSTEM-IMAGES-02        none    bind    0    0
#
#
# END OF BINDINGS 
```

---

### Post by TheFu on 2017-08-10
So this is an NFS SERVER ... did you move the **exports** file over too?

The numbers at the end of each line don't mean what you thnk they mean.  From the fstab manpage:
```
       The fifth field (fs_freq).
              This field is used for these filesystems by the dump(8)  command
              to  determine which filesystems need to be dumped.  If the fifth
              field is not present, a value of zero is returned and dump  will
              assume that the filesystem does not need to be dumped.
```

Some lines are missing the 6th field. I'd fix that, rather than trust the default is ok.

I don't use bind mounts.
I don't put manually mounted storage under /media/ either.  That area is for automatically mount, temporary storage - like USB flash drives, IMHO.  Lots of people use /media, so it isn't as dangerous as it was, but I've got habits from being burned.

---

### Post by mike.lussier on 2017-08-10
I dont know why the post combined the 5th and 6th fields. 
They are read as like this on the system the 6th field increments by one for each drive. 
however I'm looking at changing field 6 to 2 on all of the NAS drives. I haven't done it yet and tested. 

defaults      0       10

defaults      0       11

---

### Post by mike.lussier on 2017-08-10
Upgraded all the way to 17.04. BIG MISTAKE ! . The system sees all of the drives a ZFS and states that there is nothing on them. reverting back to 15 code. so much for upgrading. 
Such a waste of time. what the hell has happened to the code ???

---

### Post by QIII on 2017-08-10
Hello!

Did you reinstall at each step or did you upgrade in place?

If the latter, then you upgraded from what is now an unsupported release and likely produced an imperfect system.  Upgrading from a problematic system further compounded the problems.

Going back to 15.10 is fruitless.  As I said, it is no longer supported.

---

### Post by TheFu on 2017-08-10
> **mike.lussier said:**
> I dont know why the post combined the 5th and 6th fields. 
They are read as like this on the system the 6th field increments by one for each drive. 
however I'm looking at changing field 6 to 2 on all of the NAS drives. I haven't done it yet and tested. 

defaults      0       10

defaults      0       11

The only valid values for the 6th field are 0, 1, 2.  I have no idea what the values you use will accomplish or break.
From the manpage:
```
       The sixth field (fs_passno).
              This field is used by the fsck(8) program to determine the order
              in which filesystem checks are done at reboot  time.   The  root
              filesystem  should be specified with a fs_passno of 1, and other
              filesystems should have a fs_passno of 2.  Filesystems within  a
              drive will be checked sequentially, but filesystems on different
              drives will be checked at the same time to  utilize  parallelism
              available in the hardware.  If the sixth field is not present or
              zero, a value of zero is returned and fsck will assume that  the
              filesystem does not need to be checked.
```
Wish it was clearer and I didn't look at the code.  For all I know, it could check for 0, 1 and then assume all other values are 2. IDK.  But out of bounds values are confusing and might change in unexpected ways across different implementations - like when systemd takes over fsck in a few years.

---

### Post by mike.lussier on 2017-08-14
The 6th filed was all changed to 2. Thank you for the catch. That still din't help anything. I have changed up to 16.04 now and I'm using ZFS. 
The reason for putting all of the drives into the FSTAB file was to insure that their mount came up connected with the proper drive. without it my music drive connected to movies and documents to tv shows and have you ever tried to watch a PDF file on TV ??

---

### Post by TheFu on 2017-08-14
I've never used ZFS on Linux.  Think you need to always mention that when posting.

---

