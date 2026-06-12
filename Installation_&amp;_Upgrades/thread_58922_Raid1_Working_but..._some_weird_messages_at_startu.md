---
title: "Raid1 Working but... some weird messages at startup."
date: 2005-08-22
forum: Installation &amp; Upgrades
---

### Post by Yann2 on 2005-08-22
So, first, I've got 2 raid1, one for my /home and one for /mnt/secure:
/dev/md0              5,5G  3,2G  2,1G  61% /home
/dev/md1               37G  7,8G   28G  23% /mnt/secure

They both seems to be working pretty well.


yann@yannpc:~$ cat /proc/mdstat
Personalities : [raid1] 
md1 : active raid1 dm-8[1] dm-7[0]
      39061888 blocks [2/2] [UU]
      [===>.................]  resync = 17.1% (6711360/39061888) finish=535.8min speed=1004K/sec
md0 : active raid1 dm-6[1] dm-5[0]
      5855552 blocks [2/2] [UU]
      
unused devices: <none>




But, at boot, I get some messages like "fsck error: md0 not found"
It tells me it is a critical error, and I should enter my admin password to correct the filesystem manually, or ctrl+d to contnue to boot. When entering ctrl+d, the systems starts up, and both raids seems to work.
When entering the admin password, fsck.ext3 /dev/md0 tells me "/home is clean".

Here is the dmesg:


md: bind<dm-5>
md: bind<dm-6>
raid1: raid set md0 active with 2 out of 2 mirrors
md: bind<dm-7>
md: bind<dm-8>
md: md1: raid array is not clean -- starting background reconstruction
raid1: raid set md1 active with 2 out of 2 mirrors
..<6>md: syncing RAID array md1
md: minimum _guaranteed_ reconstruction speed: 1000 KB/sec/disc.
md: using maximum available idle IO bandwith (but not more than 200000 KB/sec) f
or reconstruction.
md: using 128k window, over a total of 39061888 blocks.
md: resuming recovery of md1 from checkpoint.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on md0, internal journal
EXT3-fs: mounted filesystem with ordered data mode.


Thanks for help  :-|

---

### Post by tonym on 2005-08-22
This is a common problem with hoary.  Two things you might try that work for me but can't promise they won't cause problems.

Firstly,  delete /etc/mdadm/mdadm.conf.  Honest,  things still work!

Also, add "sleep 5" to the start of the /etc/init.d file for fsck - can't remember exact name and I'm using a Windows PC.

---

### Post by Yann2 on 2005-08-22
Deleting mdadm.conf solved the problem... Many thanks :)

---

### Post by Yagisan on 2005-08-22
[QUOTE=tonym]This is a common problem with hoary.  Two things you might try that work for me but can't promise they won't cause problems.[/quote] very true [QUOTE=tonym]Firstly,  delete /etc/mdadm/mdadm.conf.  Honest,  things still work![/quote] Regetablly that doesn't always work. An alternate sollution can be found here [http://bugzilla.ubuntu.com/show_bug.cgi?id=4944#c6](http://bugzilla.ubuntu.com/show_bug.cgi?id=4944#c6) if deleting  mdadm.conf doesn't work

---

