---
title: "Cleaning after upgrade"
date: 2010-10-09
forum: Installation &amp; Upgrades
---

### Post by pjalegria on 2010-10-09
Hi

I just upgrade my 10.04 Netbook Remix to 10.10 Netbook Edition and is missing 500mb on my 4gb SSD... is there any way to be some TMP files from de upgrade? how can i delete them?

THX

---

### Post by mikewhatever on 2010-10-09
I think 
```
sudo apt-get clean
```

---

### Post by CharlesA on 2010-10-09
Try running this to see where the most data on your drive is:

```
du -h --max-depth=1 / 2> /dev/null
```

Note: the 2> /dev/null is there to get rid of the "permission denied" messages when it tries to work thru /proc.

---

### Post by pjalegria on 2010-10-09
> 32K	/media
4,0K	/selinux
11M	/etc
6,5M	/bin
0	/proc
69M	/opt
124K	/tmp
4,0K	/root
134M	/lib
504K	/dev
119M	/home
4,0K	/mnt
22M	/boot
4,0K	/cdrom
4,0K	/srv
0	/sys
317M	/var
6,2M	/sbin
2,1G	/usr
16K	/lost+found
2,8G	/


317M	/var is this normal???

---

### Post by CharlesA on 2010-10-09
It's probably yer package cache.

```
sudo apt-get autoremove
```

---

### Post by pjalegria on 2010-10-09
still 317M /var after "sudo apt-get autoremove"...

---

### Post by CharlesA on 2010-10-09
Then that's the best you can do. /var stores the package cache (more specifically /var/cache/apt/archives/). If you want to delete the debs there, there shouldn't be any problems outside of having to download them again if they are needed.

---

