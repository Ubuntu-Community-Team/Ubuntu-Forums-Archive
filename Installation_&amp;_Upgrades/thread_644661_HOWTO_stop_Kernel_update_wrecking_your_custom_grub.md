---
title: "HOWTO stop Kernel update wrecking your custom grub menu.lst"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by RIchard James13 on 2007-12-19
Recently I had installed a Kernel update, after rebooting I found that not only would Ubuntu not boot but it had removed all the other OS'es I had in my menu.lst

So I did a bit of research on this subject and looked at the settings of the /boot/grub/menu.lst file and I discovered how to stop a kernel update from ruining my menu.lst

**Step 1) change groot**

There is an option for groot in your menu.lst this should be set to where your current Ubuntu / partition is. For example if groot is
```

# groot=(hd0,0)
```
Then /dev/hda1 or /dev/sda1 MUST be where / is mounted
To find out where / is mounted issue the following command at the prompt
```

$ mount | grep on./.type
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
```

To understand how Linux drive mapppings convert to grub drive mappings
i.e. that /dev/sda1 is (hd0,0)
Use the following table and the following rules
[LIST]
[*]Grub starts counting drives from 0 but skips every optical drive (so if you have a DVD at /dev/hdb then grub will make a drive at /dev/hdc 1 instead of 2)
[*]Linux starts counting drives at a and goes through the alphabet
[*]Grub starts counting partitions at 0
[*]Linux starts counting partitions at 1
[/LIST]
*Note: originally in Linux drives marked /dev/hd? were IDE drives and those marked /dev/sd? were SCSI drives. However due to changes in the kernel it is possible to have IDE drives named /dev/sd?*
```

Linux Partitions                    Grub Partitions
/dev/hda1        /dev/sda1          (hd0,0)
/dev/hdb1        /dev/sdb1          (hd1,0)
/dev/hdc1        /dev/sdc1          (hd2,0)
/dev/hdd1        /dev/sdd1          (hd3,0)

/dev/hda1        /dev/sda1          (hd0,0)
/dev/hda2        /dev/sda2          (hd0,1)
/dev/hda3        /dev/sda3          (hd0,2)
/dev/hda4        /dev/sda4          (hd0,3)
/dev/hda5        /dev/sda5          (hd0,4)
/dev/hda6        /dev/sda6          (hd0,5)

/dev/hdc5        /dev/sdc5          (hd2,4)
```

So my /dev/hda3 maps to (hd0,2)

Then I get that value and copy it into the groot line in menu.lst
```

# groot=(hd0,2)
```

*Note: it is okay to have the comment character (#) at the beginning of the groot line*

[B]Step 2) Change kopt=root=UUID=e7cf76ab-c3bf-468a-8359-a77f65d99346 ro
[/B]
There is another option for kopt this has the parameters that are passed to the kernel. The most important one here is the root parameter. This can be given to the Kernel as a UUID (Unique Identifier for a partition and disk) or as a straight linux drive mapping like /dev/sda3. It is preferable to use UUIDs since they can be used if drives are swapped around.
This is what kopt on my system looks like.
```

# kopt=root=UUID=e7cf76ab-c3bf-468a-8359-a77f65d99346 ro
```
to find out the UUID for my system I again look at my / partition
```

$ mount | grep on./.type
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
```
That will give me something like /dev/hda3 yours will probably be different
I then look for the UUID of /dev/hda3 as follows. Please insert your drive mapping in here.
```

$ sudo vol_id -u /dev/hda3
e7cf76ab-c3bf-468a-8359-a77f65d99346
```

Then I get that value and copy it into the kopt line in menu.lst
# kopt=root=UUID=[COLOR="SeaGreen"]e7cf76ab-c3bf-468a-8359-a77f65d99346[/COLOR] ro
Where the value in [COLOR="SeaGreen"]Green[/COLOR] is the bit I alter

*Note: it is okay to have the comment character (#) at the beginning of the kopt line*

**Step 3) Move the lines for other operating systems out of the way**

When the kernel gets updated everything between
```

## ## End Default Options ##

....... and ..............

### END DEBIAN AUTOMAGIC KERNELS LIST
```
Gets rebuilt from the settings above for instance if you delete everything between those two lines then a kernel update puts back in the three Ubuntu boot options.

```
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e7cf76ab-c3bf-468a-8359-a77f65d99346 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e7cf76ab-c3bf-468a-8359-a77f65d99346 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Note that it uses my groot to get (hd0,2) and my kopt to get UUID=e7cf76ab-c3bf-468a-8359-a77f65d99346

So if you have any settings for any other operating system, including other Linux installs or even other Ubuntu installs move them below the line that says.
```

### END DEBIAN AUTOMAGIC KERNELS LIST
```
For example in my system it looks like this
```

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Slackware 11
root		(hd0,1)
kernel		/boot/vmlinuz root=/dev/hda2 ro

title		Slackware 11-Safe
root		(hd0,1)
kernel		/boot/safe root=/dev/hda2 ro single

title		WinXP
rootnoverify	(hd0,0)
makeactive
chainloader +1
```

Please point out any mistakes in my post.

---

