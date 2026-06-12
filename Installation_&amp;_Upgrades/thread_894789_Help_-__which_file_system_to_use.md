---
title: "Help -  which file system to use?"
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by _Horus_ on 2008-08-19
I am putting Ubuntu onto a server, that will act as a storage centre and media server. I intend to use something like rsync to send data to the server on a reasonably regular basis.

PROBLEM: I want my laptop (XP) to be able to access and use the data on the server (sever will stay on but PC won't). Do I have to ensure that my server is setup in Ext3 or something else so that the laptop can use the data on it? Will the server be able to deal with the NTFS based data from the PC? I see that there are several file systems: Ext2,3 and 4 (is this available yet), XFS etc.

Thanks very much for any help you can give me!:)

Oh yeah, the server will hopefuly stream media to the PS3. I guess the data will also have to be in NTFS format so please can you extend your answer to that too? Thanks very much!!

---

### Post by ilrudie on 2008-08-19
ext 3 is probably the best bet (and most supported here on the forums).  You will need to set up samba or ftp in order to have the windows box read and write data to the share.  I don't think windows plays nice with NFS (Linux/Unix native) but there may be something out there.

Try ushare for streaming to the PS3.  I believe ushare can handle this and it is relatively easy to setup.

There is not a "NTFS format".  Its just a file system.  It tracks and store files.  NTFS is just different, inferior, outdated and not native to Linux.

---

### Post by _Horus_ on 2008-08-19
Thanks *ilrudie*. I guess I'll use Ext3.
I heard that Samba is a bit naff and that rsync is a much better tool to use for backing up data from a non-lynux machine to a lynux machine. If you have any feedback on that then it would help me on deciding which to use (even an alternative would be fine).

I'll look into ushare, thanks!

---

### Post by ilrudie on 2008-08-19
If you are just looking for backups of you windows box check out bacula.  I don't know if there is rsync for windows.

---

