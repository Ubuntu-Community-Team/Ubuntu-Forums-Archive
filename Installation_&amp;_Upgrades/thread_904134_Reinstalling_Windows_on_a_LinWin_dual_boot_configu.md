---
title: "Reinstalling Windows on a Lin/Win dual boot configuration"
date: 2008-08-29
forum: Installation &amp; Upgrades
---

### Post by Qwertinsky on 2008-08-29
I followed some bad advice in some other forum on speeding up Windows on my Eee900.

Now I am left with no other option then to reinstall Windows.

My biggest concern is Windows is going to stomp out Grub and make Ubuntu inaccessible.

What is the easiest way to restore Grub after Windows has wiped it out?

Eeepc 900
Ubuntu 8.04
Windows XP Pro SP3

---

### Post by cariboo on 2008-08-29
Windows will overwrite the master boot record.

You could use your livecd to reinstall grub:

First you have to chroot your installation:

```
sudo mount /dev/sda2 /mnt
```

Then

```
sudo chroot /mnt
```

Then

```
sudo apt-get --reinstall grub
```

You should be able to dual boot after this.

Jim

---

### Post by lswest on 2008-08-29
or you could do this:
For GRUB restore to MBR:
boot to the LiveCD (this is the easiest way IMHO) and then start a terminal (applications-->accessories-->terminal)and type:

    ```
sudo grub
    find /boot/grub/stage1
    root (hd?,?)
    setup (hd?)
    quit
```


where the (hd?,?) and (hd?) corresponds to the output of find /boot/grub/stage1 (first time round the (hd?,?) stands for the drive (hd?) and the partition (,?) at which Ubuntu (or any Linux) is located, and then the second time round (hd?) just stands for the drive, for the MBR).
If you would like a more detailed explanation catlett did a good job with his how-to here and also offers troubleshooting ideas.

How to restore GRUB to a partition:
**DISCLAIMER** This is untested, as I haven't had time to do so yet, but it should work. Any feedback would be great, either by PM on UF or to have a reply posted here.

    ```
sudo grub
    find /boot/grub/stage1
    root (hd?,?)
    setup (hd?[COLOR="Red"],?[/COLOR])
    quit
```

(for an explanation of the above code, see the info on restoring GRUB to the MBR, apart from the code marked in bold).
There is only one small variation for this (marked in red) but it's a significant one. That "?" marked in red should be the same one you used for your "root" command in the line above. It will then install GRUB to that partition.

I copied it off my [blog's howto]("http://lswest-ubuntu.blogspot.com/2008/06/installing-bootloader-how-to.html") (I'm a lazy guy :P), but either method should work, I always prefer this one (specifically, the first half, since I install boot to the MBR, not a partition) since I usually have no internet connection on the liveCD.

---

### Post by tuxerman on 2008-08-29
I just finished replying to a same query.
Check this post[URL="http://ubuntuforums.org/showthread.php?t=224351"]:
http://ubuntuforums.org/showthread.php?t=224351[/URL]
Have a good day

---

