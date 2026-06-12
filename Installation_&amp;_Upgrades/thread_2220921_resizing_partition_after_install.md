---
title: "resizing partition after install"
date: 2014-04-29
forum: Installation &amp; Upgrades
---

### Post by viniosity on 2014-04-29
The default xubuntu installer gave me a single giant partition that I'd like to separate after the fact. I booted from a live CD and ran gparted (as root) but it says that my main partition is using all but 36MB of space and so won't let me resize it.

I'm on my laptop now and df -h shows I'm only using 13%. Any thoughts on why gparted won't see the same thing? The version I ran is based on parted 2.3 iirc.

```

Filesystem                    Size  Used Avail Use% Mounted on
/dev/mapper/xubuntu--vg-root  450G   52G  376G  13% /
none                          4.0K     0  4.0K   0% /sys/fs/cgroup
udev                          3.9G  4.0K  3.9G   1% /dev
tmpfs                         790M  1.4M  788M   1% /run
none                          5.0M     0  5.0M   0% /run/lock
none                          3.9G   21M  3.9G   1% /run/shm
none                          100M   28K  100M   1% /run/user
/dev/sda2                     237M   88M  137M  40% /boot
/dev/sda1                     487M  3.5M  483M   1% /boot/efi

```

---

### Post by Bucky Ball on 2014-04-29
Boot from the LiveCD, open Gparted, right click your giant partition and make sure it is unmounted. You should then be able to resize. It needs to be unmounted (and generally is when you boot from a LiveCD, unless you mount the partition manually). ;)

---

### Post by viniosity on 2014-04-29
Booted from the live cd and right clicked. No option to unmount but there is an option to "Deactivate" which I selected. I'm then able to "check" the partition (which I "applied") Still shows the partition as full.

I couldn't take a screenshot from the live cd but I've got a smartphone snapshot: [http://imgur.com/9egoywr](http://imgur.com/9egoywr)
[IMG]http://i.imgur.com/9egoywr.jpg[/IMG]

---

### Post by Bucky Ball on 2014-04-30
No idea how you've set this up. sda1 is a fat32 partition. Why? sda2 is EXT2, a totally obsolete filesystem (EXT4 is the current), and sda3 is a filesystem I know nothing about with a mountpoint that makes no sense to me. Along with this, there is no /swap partition. I can't imagine an Xubuntu default partitioning would have come up with this ...

The option to resize that partition is there and available. Just wondering what happens if you try it. If this is a new install with little alteration, I would suggest backing up anything you need to and trying to install again, this time choosing 'Something Else' when you get to the partitioning section and manually setting things up as you want them. 

/ = should be an EXT4 partition;
/home = EXT4 and is a storage partition which also contains your user settings;
/swap = 2Gb is fine. 

You could put all of this inside an extended partition or make / a primary partition, /home a logical partition.

You say the 'Xubuntu default install' set things up like this. Did you click the option for Xubuntu to set it up automagically when you got to that section of the install?

PS: This:

```
/dev/mapper/xubuntu--vg-root  450G   52G  376G  13% /
```

... indicates the whole partition is not being used so I suggest trying to resize it and see if gparted lets you. May just be a glitch with the 'wet behind the ears' 14.04 LTS and gparted. What does the gparted in the actual install (not the livecd version) tell you? Any different?

---

### Post by Elfy on 2014-04-30
Not sure that you can use gparted to resize lvm systems.

---

