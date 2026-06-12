---
title: "Ubuntu trashed Vista?"
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by winter7 on 2006-10-20
I thought this should be easy but... I partitioned my hard drive like this:

3GB NTFS (For windows swap)
1GB Linux Swap (For Ubuntu)
70GB NTFS (For Vista)
30GB Ext3 (For Ubuntu)

I installed vista first, and that booted up fine.
I installed Ubuntu. Ubuntu boots up fine.
I went to add vista to GRUB, thinking it should be simple.
Only problem is that it shows UBUNTU as hd(0,2)... huh???? I'm confused. How do I get Vista to boot up again?

TIA
-Dino

---

### Post by yota on 2006-10-20
Are you sure you've installed ubuntu on the 4th partition?
To check do:
```

yota@linbook:~$ sudo mount
Password:
/dev/hda4 on / type ext3 (rw,errors=remount-ro)

```
you should have / on /dev/hda4

if it's on hd3... sorry pal, but you installed ubuntu right over vista :( and have to start over.

If / is on hda4 and vista is still there, just look if /boot/grub/menu.lst contains a section like this:
> 
title           Microsoft Windows Vista Ultimate
root            (hd0,2)
savedefault
makeactive
chainloader     +1

if the section is missing just add it at the bottom of the file.

Hope this helps!

---

### Post by winter7 on 2006-10-20
Thanks for your reply!

I don't *think* I did that... 
I could of course be wrong and will try what you suggested later since I am not currently at that computer.

I say this because I have an icons for the 2 ntfs partitions on the ubuntu desktop, and when I browse to it I can see the windows and program files folders... I also have a boot folder which looks like it came from ubuntu, as well as a bootsect.bak file.

So unless ubuntu is running on an NTFS partition alongside vista somehow :???: I'm pretty sure everything is where they should be.

in menu.lst currently there is no vista entry whatsoever, and the ubuntu entries (memtest etc.) are all set to hd(0,2)

Thanks
-Dino

---

### Post by yota on 2006-10-20
Ok, if you have the two icons on the desktop everything it's fine, then there must be some confusion abot the partitions layout.
Since windows partitions are mounted the mount command will show you not only about the linux root filesystem but about them too.

You can have a look at
```

sudo fdisk -l

```
to see the actual partitions on the disk along with their names.

Finally adjust the (hd0,2) entry accordingly in the section I posted above and insert it in /boot/grub/menu.lst.
Then you will be able to boot windows again!

---

### Post by winter7 on 2006-10-20
fdisk -l

That gave me a listing and helped big time!

Apparently linux re-arranged the drive numbers a bit and lists vista as hd1. I fixed menu.lst and everything is happy now.

Gold star for you, and thanks for your help and that tip!
-Dino

---

