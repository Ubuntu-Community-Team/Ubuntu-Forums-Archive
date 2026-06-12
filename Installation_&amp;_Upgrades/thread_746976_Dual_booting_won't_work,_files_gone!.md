---
title: "Dual booting won't work, files gone!?"
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by Fzang on 2008-04-06
I installed ubuntu on my secondary harddisc but now it seems like I deleted windows or something!

When I turn on my computer and press ESC for boot options, there's only linux boot! Have I deleted windows??? If I have I'm definetly going to kill myself, because tons of schoolwork was there

What can I do to check if I deleted or not? I'm so freaking crapping myself of fear

---

### Post by Partyboi2 on 2008-04-06
Boot the ubuntu live disk and when you get to the desktop open a terminal (Applications>Accessories>Terminal) and type
```
fdisk -l
``` (Small L) then look for the windows partition, if unsure post back the results.

---

### Post by Fzang on 2008-04-06
Disk -l doesn't give me options, it just makes another line

Also, I installed it by OPENING the CD and then pressing wubi.exe or something, instead of starting it normally. Is that bad?

---

### Post by Partyboi2 on 2008-04-06
Sorry! You need to do the command with sudo infront so it would be
```
sudo fdisk -l
```

---

### Post by Fzang on 2008-04-06
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6c062a24

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         973     7815591   83  Linux
/dev/sda2             974        1216     1951897+  82  Linux swap / Solaris
johannes@johannes-laptop:~$

---

### Post by Sef on 2008-04-06
> When I turn on my computer and press ESC for boot options, there's only linux boot! Have I deleted windows??? If I have I'm definetly going to kill myself, because tons of schoolwork was

Yes, you did delete it.  However, you may be able to get it back.  

1) Don't use that computer, if possible.  If you have to, then use the Live CD and don't download or save anything to the hard drive.   The files may still be there, but if you download or save to the hard disk, you could write over the files you want to recover.

2) Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").  It can recover lost partitions.

---

### Post by talsemgeest on 2008-04-06
But he said he installed it to another drive. Shouldn't there be an sdb there somewhere?

---

### Post by Sef on 2008-04-06
> But he said he installed it to another drive. Shouldn't there be an sdb there somewhere?

I believe he meant to install it to sdb; however, he installed it to sda instead.

---

### Post by talsemgeest on 2008-04-06
Oh, well thats a nasty problem indeed...

---

### Post by Fzang on 2008-04-06
Sorry, I'm new to this but... how do I use it? I downloaded it and now I have a folder

EDIT: I just checked filesystem and it says I have 8 GB space in total, wtf?

---

### Post by Fzang on 2008-04-06
Bump

Still haven't been able to find any files, and I have a disc space of 8 GB, what the heck?

---

### Post by Partyboi2 on 2008-04-06
> **Fzang said:**
> Bump

Still haven't been able to find any files, and I have a disc space of 8 GB, what the heck?
What happened when you tried to use testdisk to recover the windows partition?

---

