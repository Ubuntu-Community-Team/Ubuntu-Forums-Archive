---
title: "Have a read-only filesystem after upgrade to Hardy"
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by blindgaenger on 2008-07-06
Hi,

I just upgraded to Hardy and run into some problems. Without touching it, my root was set to read-only. So GDM failed, because no log, tmp, etc. files could be written, of course.

I had a look at my fstab and saw it's mounted read-only on errors. (which is the default in ubuntu).
```

# /dev/sda3
UUID=76462b60-7459-4689-8b01-74fe1dd36455 /               ext3    rw,errors=remount-ro 0       1

```

Unfortunately I couldn't find an error in the logs. So I just changed it to continue on errors:
```

# /dev/sda3
UUID=76462b60-7459-4689-8b01-74fe1dd36455 /               ext3    rw,errors=continue 0       1

```

But this didn't helped! The only way to get to my desktop is to remount from the command line. This does the trick:
```

$ sudo mount -o remount,rw /
$ sudo /etc/init.d/gdm restart

```

But I'm not happy with that, because it's a hack! My system should boot without my helping hands.

Any ideas out there? Thanks!

---

### Post by PmDematagoda on 2008-07-06
Do you have the Ubuntu Live CD? If so, boot the Ubuntu Live CD and then perform an fsck on the drive:-
```
sudo e2fsck -f /dev/drive/partition-location
```

After that is done, see if the Ubuntu root partition now mounts properly.

---

### Post by blindgaenger on 2008-07-06
Thanks, I tried that. But fsck didn't found errors and the problem is still there.

Which steps are performed when a partition is mounted? And why can the 'continue' entry in the fstab be ignored?

Any ideas?

---

### Post by PmDematagoda on 2008-07-06
Just remove the 'errors=something' line and see if it makes an improvement,but you may have to be careful with this since there must be a reason why Ubuntu is mounting root as read-only.

---

### Post by pewjumper on 2008-07-07
I am wondering if this has something do do with the fact I have installed Ubuntu a half a dozen times? Mine comes up with auto fsck but if I exit (esc) it boots normally. Also if I hit (esc) before this I have 4 choices to boot from. Is there some sort of regclean? When I reinstalled did it leave dead boot records on the drive?:popcorn:

---

### Post by pewjumper on 2008-07-07
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=62949786-70b5-48a9-8b25-397057b7f7f4'
donald@donald-laptop:~$

---

### Post by pewjumper on 2008-07-07
What is the best way to totally wipe the drive and install completely new Ubuntu?:popcorn::popcorn::popcorn:

---

### Post by PmDematagoda on 2008-07-07
> **pewjumper said:**
> What is the best way to totally wipe the drive and install completely new Ubuntu?:popcorn::popcorn::popcorn:

Your problem may be an incorrect UUID, when you boot the Ubuntu Live CD and execute:-
```
sudo blkid
```
check if the results shown match those in you /etc/fstab file.

---

