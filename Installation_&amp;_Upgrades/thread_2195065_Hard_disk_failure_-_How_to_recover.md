---
title: "Hard disk failure - How to recover?"
date: 2013-12-22
forum: Installation &amp; Upgrades
---

### Post by traceur.fin on 2013-12-22
My 12.04 server began giving EXT4-fs errors and some services stopped working(DHCP etc). So I booted the system -> disk errors and fixing them didn't help. I ended up with

```
mount: / not mounted or bad option
mountall: mount / [1094] terminated with status 32
mountall: Filesystem could not be mounted: /
```

...so i guess my old 81GB hard drive has finally failed.

I also have a 2TB hard drive, which contains some partitions( /home, /var, maybe others too. Can I check that out without live CD?). 

Fortunately, I had backup script running once a week backing up other partitions to the 2TB storage.

Now, how to start recovering the server? Of course I'll buy an SSD once I'm sober to drive, but then what? Install a fresh system or somehow copy those backup partitions in there directly? Burn a live CD?

Thanks for your help!

---

### Post by fantab on 2013-12-22
Fresh Install sounds like a good idea since your data is backed up.

---

### Post by TheFu on 2013-12-22
The method used for the backup determines the method required for the restore.  Just copying files off means you'll just copy files back, I guess.

Here's a high level way to perform backups AND restores that you might consider in the future: [http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview](http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview)  Minimal storage used and very fast for backups. Restoring a base system is about 20-30 minutes ... data will take longer or shorter depending on the amount.

---

### Post by traceur.fin on 2013-12-30
I installed a fresh new 12.04 system on SDD.

After installing lvm2 it shows 4 volumes on the 2TB HDD storage: 

```

root@ressu:~# lvm lvs
  LV   VG    Attr   LSize   Origin Snap%  Move Log Copy%  Convert
  root ressu -wi-a-   1.79t
  swap ressu -wi-a- 952.00m
  tmp  ressu -wi-a-   9.31g
  usr  ressu -wi-a-  18.62g
```

I can mount tmp and usr volumes, but root gives error:

```

root@ressu:~# mount /dev/mapper/ressu-root /media/asd
mount: wrong fs type, bad option, bad superblock on /dev/mapper/ressu-root,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

```

root@ressu:~# dmesg | tail
[ 5097.757734] EXT4-fs (dm-4): ext4_check_descriptors: Checksum for group 0 failed (18220!=57130)
[ 5097.760119] EXT4-fs (dm-4): group descriptors corrupted!


```

I have run e2fsck on the root volume. After 16 hours it completed, but same error continues. I tried restoring the superblock from first backup with instructions described here:

[http://www.webdesignblog.asia/operating-systems/linux-os/ext4-fs-group-descriptors-corrupted-cannot-mount-disk-using-ubuntu/#sthash.cORtSpeL.dpbs](http://www.webdesignblog.asia/operating-systems/linux-os/ext4-fs-group-descriptors-corrupted-cannot-mount-disk-using-ubuntu/#sthash.cORtSpeL.dpbs)

...but it just seemed to start the 16h progress again. Should I let it run and will the result be any different?


Any ideas how to recover "root" volume? Is it missing something that went with the failed hard drive and LVM volumes in there?

E: also, lvm volumes were encrypted with LUKS. First opened the encrypted partition with cryptsetup luksOpen.

---

### Post by traceur.fin on 2014-01-10
Still haven't figured out anything... Have I completely lost the /root volume?

---

