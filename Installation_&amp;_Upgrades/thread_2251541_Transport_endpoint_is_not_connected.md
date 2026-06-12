---
title: "Transport endpoint is not connected"
date: 2014-11-04
forum: Installation &amp; Upgrades
---

### Post by memilanuk on 2014-11-04
Recently replaced 14.04 with 14.10 on a dual-boot laptop (Win7 and Ubuntu).  Main HDD is where all the OS/user directories are, second HDD is storage for things that need to be accessible to both, and is formatted ntfs.


Previously, everything was working more or less fine.  After doing a fresh install from a USB stick, I proceeded to re-install various apps, etc.  Kept getting system problem warnings regarding a kernel oops.  When I got around to VirtualBox, I noticed it was hanging up and having some difficulties.  When I went to start working with vagrant, I wanted to cd to the data directory on the 2nd HDD:


    ```
monte@machin-shin:~$ cd /srv/data
    bash: cd: /srv/data: Transport endpoint is not connected
    monte@machin-shin:~$
```


and I'm finding this sort of thing in /var/log/kern.log:


    ```
monte@machin-shin:~$ grep ntfs /var/log/kern.log 
    Nov  4 11:45:58 machin-shin kernel: [  178.834311] ntfs: driver 2.1.30 [Flags: R/O    MODULE].
    Nov  4 13:40:30 machin-shin kernel: [ 6828.786153] CPU: 3 PID: 768 Comm: mount.ntfs Tainted: G           OE 3.16.0-24-generic #32-Ubuntu
    Nov  4 13:40:30 machin-shin kernel: [ 6828.790793] note: mount.ntfs[768] exited with preempt_count 2
    Nov  4 14:03:53 machin-shin kernel: [ 1217.788636] CPU: 2 PID: 525 Comm: mount.ntfs Tainted: G           OE 3.16.0-24-generic #32-Ubuntu
    Nov  4 14:03:53 machin-shin kernel: [ 1217.797175] note: mount.ntfs[525] exited with preempt_count 2
    Nov  4 14:41:40 machin-shin kernel: [  174.853678] CPU: 3 PID: 777 Comm: mount.ntfs Tainted: G           OE 3.16.0-24-generic #32-Ubuntu
    Nov  4 14:41:40 machin-shin kernel: [  174.858862] note: mount.ntfs[777] exited with preempt_count 2
    Nov  4 14:56:35 machin-shin kernel: [  234.143899] CPU: 3 PID: 788 Comm: mount.ntfs Tainted: G           OE 3.16.0-24-generic #32-Ubuntu
    Nov  4 14:56:35 machin-shin kernel: [  234.149761] note: mount.ntfs[788] exited with preempt_count 2
    monte@machin-shin:~$ 

```



Does anybody have any idea what is going on here?  If this is the way 14.10 is going to start out, I'm likely to be re-installing 14.04 fairly soon.

---

