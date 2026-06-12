---
title: "Package operation failed"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by griztown on 2011-04-20
I'm using 10.10 and need to update my kernel apparently to 2.6.35.  When I do, I get the package operation failed message box.  

```
installArchives() failed: Preconfiguring packages ...

Preconfiguring packages ...

(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 151651 files and directories currently installed.)

Preparing to replace linux-image-2.6.35-28-generic 2.6.35-28.49 (using .../linux-image-2.6.35-28-generic_2.6.35-28.50_amd64.deb) ...

Done.

Unpacking replacement linux-image-2.6.35-28-generic ...

dpkg: error processing /var/cache/apt/archives/linux-image-2.6.35-28-generic_2.6.35-28.50_amd64.deb (--unpack):

 failed in write on buffer copy for backend dpkg-deb during `./lib/modules/2.6.35-28-generic/kernel/fs/xfs/xfs.ko': No space left on device

No apport report written because MaxReports is reached already
dpkg-deb: subprocess paste killed by signal (Broken pipe)

Examining /etc/kernel/postrm.d .

run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic

run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic

Preparing to replace libslp1 1.2.1-7.7 (using .../libslp1_1.2.1-7.7ubuntu0.1_amd64.deb) ...

Unpacking replacement libslp1 ...

Errors were encountered while processing:

 /var/cache/apt/archives/linux-image-2.6.35-28-generic_2.6.35-28.50_amd64.deb

Setting up libslp1 (1.2.1-7.7ubuntu0.1) ...

Processing triggers for libc-bin ...

ldconfig deferred processing now taking place


```

It says there's no space which is surprising.  Here's a look at my drive allocation

```

$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/vg_main-root
                        472036    361741     85924  81% /
none                   4081080       360   4080720   1% /dev
none                   4088464       248   4088216   1% /dev/shm
none                   4088464       352   4088112   1% /var/run
none                   4088464         0   4088464   0% /var/lock
/dev/mapper/vg_main-tmp
                        472036     10636    437029   3% /tmp
/dev/md0                377767     50381    307882  15% /boot
/dev/mapper/vg_main-var
                       4805760   1002960   3558680  22% /var
/dev/mapper/vg_storage-storage
                     480428776  42882724 413141676  10% /data
/dev/mapper/vg_main-usr
                       9611492   2606832   6516420  29% /usr
/dev/mapper/vg_main-home
                     449860320  67709644 359299092  16% /home

```

So perhaps my vg_main-root is too small?

---

### Post by griztown on 2011-04-21
Any suggestions?

---

### Post by tommcd on 2011-04-22
I always run *df -h*, since it is more easily readable by us humans (-h) :)
It may be that your root partition is too small. Remember that some space on each partition is reserved in case the partition gets to be too full, so that an admin can login and fix things.
Try running:
```
sudo apt-get autoremove
sudo apt-get clean
```
This may free up enough space so you can upgrade if that is indeed the problem.
Is this system a server or something? I am just wondering why you have separate /, /var, /usr, /data, and /home partitions.
Is this a RAID array?

---

### Post by griztown on 2011-04-25
Thanks for the help.  Here's what df -h looks like.

```

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/vg_main-root
                      461M  353M   85M  81% /
none                  3.9G  360K  3.9G   1% /dev
none                  3.9G  1.1M  3.9G   1% /dev/shm
none                  3.9G  352K  3.9G   1% /var/run
none                  3.9G     0  3.9G   0% /var/lock
/dev/mapper/vg_main-tmp
                      461M   11M  427M   3% /tmp
/dev/md0              369M   50M  301M  15% /boot
/dev/mapper/vg_storage-storage
                      459G   46G  390G  11% /data
/dev/mapper/vg_main-var
                      4.6G  500M  3.9G  12% /var
/dev/mapper/vg_main-usr
                      9.2G  2.5G  6.3G  29% /usr
/dev/mapper/vg_main-home
                      430G   65G  343G  16% /home

```

So it would appear I need to resize my root partition.  It's a Logical Volume so hopefully it's doable.  Any suggestions on where I should start?

---

### Post by tommcd on 2011-04-27
> **griztown said:**
> 
So it would appear I need to resize my root partition.  It's a Logical Volume so hopefully it's doable.  Any suggestions on where I should start?
I am not familiar with how to resize LVM partitions.
It seems that you could combine the root, /tmp, /var, and /usr partitions. That would make more room for updates since those partitions are nowhere near full.
Also try running the commands I gave in my last post.

---

