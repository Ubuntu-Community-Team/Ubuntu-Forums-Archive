---
title: "Removing Debian and fixing the MBR."
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by OmnificienT on 2008-08-23
Hello,

Does someone know which way I can remove Debian from my system, and then reinstall grub so that it will detect Kubuntu and Windows XP?

Thank You,

OmnificienT

---

### Post by Pumalite on 2008-08-23
Erase the partition and then reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by OmnificienT on 2008-08-23
In this post I'll explain how I removed Debian and restored the MBR. I hope it might be useful to somebody as a tutorial/guide.

Everything was done from within an already installed Kubuntu 8.04 system.

These are the steps I took:

```

cat /proc/partitons

```
This gave me an indication of the disk and partition names.

Then I used Dolphin to go to system:/media/ and found my Debian drive there (you can click it to see what's on it). I rightclicked and pressed properties.
I looked at the Meta-info tab, and saw it was known to the system as /dev/sda3

Then I opened a console and did:
```
sudo fdisk /dev/sda
```

Then I pressed "p" to print the partition table. Here I could see /dev/sda3 as a Linux partiton. 

Being sure I knew I had the proper drive I now continued. I pressed "d" to delete a partition. In this case it was the 3rd one, so I pressed 3 when it asked me which partition to delete.

The final step was to enter a "w" to write the changes.



The next step was fixing my MBR.

```
sudo grub
```
It takes a while to load. Then: 
```
find /boot/grub/stage1
```

This will return a location. Enter whatever was returned here:

```
root (hd?,?) 
```
Now install grub to the harddisk:
```
setup (hd?)
```

And finally:
```
quit
```

Then I rebooted the system and I was relieved to see grub asking me which operating system to load.

Thank you Pumalite and catlett.

---

### Post by caljohnsmith on 2008-08-23
> **OmnificienT said:**
> 
```
setup grub
```

Is that possibly a typo, OmnificienT? I believe the correct command is:
```
grub> setup (hdX)
```
Where (hdX) would be (hd0) to install Grub to the MBR of the first HDD.

---

### Post by OmnificienT on 2008-08-24
You were correct caljohnsmith, I fixed the typo. Thanks for the comment.

---

