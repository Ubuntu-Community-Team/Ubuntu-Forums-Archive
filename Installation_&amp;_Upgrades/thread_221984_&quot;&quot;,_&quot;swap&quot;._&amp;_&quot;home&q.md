---
title: "&quot;/&quot;, &quot;swap&quot;. &amp; &quot;/home&quot; partions with GUI partitioner?"
date: 2006-07-24
forum: Installation &amp; Upgrades
---

### Post by jsonder on 2006-07-24
I'm having the same problem with the Elft 1st knot that I had with the final release of Dapper. I divide a hard drive into 3 partitions: /, swap, and /home and in the past I've been able to do fresh installs in the / partition, keeping the /home partion unmodified (not reformatted)

At the transition from Dapper betas to RC1 the partitioner went "more GUI" but I've lost the ability to name the /home partition during the installation (edit partition names, defaulted to "media" by installation program).

I'm sure that there must be some simple way to do an installation to my old "/" partition and later delete the "/home" under "/" and rename my old /home partition as /home again.

Can someone tell me how to do this? At present I won't try knot 1 as I don't want to reload several gigs of photos, music, etc. again. I did that with the fresh installation of 6.0.](*,) 

John

---

### Post by richbarna on 2006-07-24
Take a look at Aysiu's guide
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by swamytk on 2006-07-24
1. Install the Dapper at it does (/ and swap only with home directory under /) and reboot. Go to shell (Ctrl+Alt+1)
2. ```
$ sudo rm -rf /home/yourlogin
```
3. make an entry in /etc/fstab for your old home partition.
4. ```
$ sudo mount /home
```
5. ```
$ cd /home
```
6. change the permission for your home directory (better to do it)
```
$ chown -R yourlogin:yourlogin yourlogin
```
7. Login with yourlogin either in shell and Graphical screen

---

### Post by jsonder on 2006-07-24
Well, it turns out that I lied, because I hadn't had the guts to delete my / partition and get on with it.  Thanks to your assistance I started and found out that renaming is still there, just buried further in the process.

The next window let me set up, name and controll formatting of all 4 partitions on 2 physical disks (hda1=/; hda2=swap; hda3=/home; hdb1=/backuup).  ** backuup mispelling is intentional to prevent other programs from defaulting to it, an old windoze habit**

Thank you.  The installation is going on right now.  If there are any problems with this approach, I will follow up in this thread.

---

### Post by jsonder on 2006-07-25
Everything has come up roses on the P4 box.  No problems.  Everything still accessible.  

John (this post accomplished using the Seamonkey browser which I can't use on the mac mini)

---

