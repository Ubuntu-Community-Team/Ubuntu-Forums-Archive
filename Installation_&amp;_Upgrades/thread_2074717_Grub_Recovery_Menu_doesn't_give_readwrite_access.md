---
title: "Grub Recovery Menu doesn't give read/write access"
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by lz1dsb on 2012-10-22
To cut the story short, because of recent issues with a distribution upgrade I did now I have to play around with the Recovery Mode. 
[http://ubuntuforums.org/showthread.php?t=2074252](http://ubuntuforums.org/showthread.php?t=2074252)

I'm able to gain access to the Recovery Mode without any issues. The problem I have is that I'm not able to gain read/write access to my filesystem. When I select the option to drop down as root, they system is still in read-only mode. When I select the fsck option the partitions are checked, and than it hangs without giving me any prompt. It's the same with the networked option. Again the partitions are checked, and it hangs without giving me any prompt to type commands into...What shall I do to gain read/write access?

---

### Post by darkod on 2012-10-22
It drops you to the root shell in read/only by default. Try something like this at the shell:
```
mount -o rw,remount /
```

If it works, that should remount it read/write.

Note that if you want to fsck the root partition or any partition that is mounted, you can't. You need to fsck from live mode because the target partition can't be mounted.

---

### Post by lz1dsb on 2012-10-22
> **darkod said:**
> It drops you to the root shell in read/only by default. Try something like this at the shell:
```
mount -o rw,remount /
```If it works, that should remount it read/write.

Note that if you want to fsck the root partition or any partition that is mounted, you can't. You need to fsck from live mode because the target partition can't be mounted.

I tried that... the command executes but than if I try 'sudo apt-get update' I get an error saying that the system was unable to lock the administration directory... suggesting that the filesystem is read-only...

---

### Post by lz1dsb on 2012-10-22
I'm closing this thread. I finally was able to get it. I'm able to gain read/write access through the "fix broken packages" menu entry. First the fsck program is started to check the consistency of all partitions and than a read/write access with network support is granted to the console. It took me a lot of time to figure that out. :guitar:

---

