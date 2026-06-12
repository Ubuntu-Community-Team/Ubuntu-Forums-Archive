---
title: "Trouble Mounting: /dev/sdx already mounted or &quot;mountpoint&quot; busy"
date: 2006-09-24
forum: Installation &amp; Upgrades
---

### Post by mnorton on 2006-09-24
Having trouble mounting a new partition to any directory:

Code:
```

root@ubuntu:/mnt# mount /dev/sdb1 /newhome mount: /dev/sdb1

already mounted or /newhome busy

```
I created and formatted (ext3) the partition using gparted


```

root@ubuntu:/# fdisk -l

Disk /dev/sda: 9105 MB, 9105018368 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1057     8490321   83  Linux
/dev/sda2            1058        1106      393592+   5  Extended
/dev/sda5            1058        1106      393561   82  Linux swap / Solaris

Disk /dev/sdb: 9105 MB, 9105023488 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1106     8883913+  83  Linux

```


```

root@ubuntu:/# mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

```

Any ideas?

Thanks,

Mark

---

### Post by Ocxic on 2006-09-25
> root@ubuntu:/mnt# mount /dev/sdb1 /newhome mount: /dev/sdb1/

of this is the actual command your tying in leave out the "mount: /dev/sdb1/" at the end of the line.

---

### Post by mnorton on 2006-09-25
> **Ocxic said:**
> of this is the actual command your tying in leave out the "mount: /dev/sdb1/" at the end of the line.

Sorry, bad editing. the actual command was:

```
root@ubuntu:/# mount -t ext3 /dev/sdb1 /newhome
```

Same result;

 mount: /dev/sdb1 already mounted or /newhome busy

---

### Post by hajk on 2006-09-25
It is bad practice to use a toplevel /newhome directory for this, and equally bad practice to do all of this as root user. You should really in a regular user terminal do (without the prompts)

$ sudo mkdir /mnt/newhome
$ sudo mount /dev/sdb1 /mnt/newhome

or (if the ext3 FS is not recognized)

$ sudo mount -t ext3 /dev/sdb1 /mnt/newhome

Let us know if this works or not.

---

### Post by mnorton on 2006-09-25
> **hajk said:**
> It is bad practice to use a toplevel /newhome directory for this, and equally bad practice to do all of this as root user. 

hajk,

Thank you for the best practices, I'll be sure to use these going forward.

I noticed that the problem started after running the 2.6.18 kernel. It must be something that I configured (or failed to). When I drop back to 2.6.15, everything works as expected.

Thanks,

Mark

---

### Post by sebbe1991 on 2006-09-25
You need to apply the bd-claim patch or mount with ```
sudo mount /dev/evms/sdb1 /newhome
```

---

### Post by mnorton on 2006-09-25
> **sebbe1991 said:**
> You need to apply the bd-claim patch or mount with ```
sudo mount /dev/evms/sdb1 /newhome
```

Thanks,

I totally see the value in what EVMS does and it makes sense if  you are deploying homogeneous linux systems in a large engironment. 

Since I'm not in an enterprise, I decided just to remove EVMS after reading this: [http://evms.sourceforge.net/convert.html]("http://evms.sourceforge.net/convert.html")

and this: [http://ubuntuforums.org/showthread.php?t=257155&highlight=bd-claim]("http://ubuntuforums.org/showthread.php?t=257155&highlight=bd-claim")

By issuing:

sudo apt-get remove evms

Thanks for pointing me in the right direction!

MN

---

