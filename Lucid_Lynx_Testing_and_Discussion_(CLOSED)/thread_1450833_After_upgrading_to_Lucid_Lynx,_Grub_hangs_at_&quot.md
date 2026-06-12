---
title: "After upgrading to Lucid Lynx, Grub hangs at &quot;Starting up&quot;"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Spaced on 2010-04-09
Hi everybody,

today I upgraded from Karmic Koala to Lucid Lynx, and during the downloading and the installation of the updates everything seemed to go well. But at the first reboot, I got the problem mentioned in the title: the operating system doesn't boot, and Grub hangs at "Starting up...".
Neither recovery mode helps: everything works well until it says

```
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Done.
```

Then nothing appears for 35 seconds, when I get this:

```
Adding 4530288k swap on /dev/sda6. Priority:-1 extents:1 across:4530288k
EXT3 FS on sda5, internal journal
```

And then everything stops forever.

I've tried to access my hard disk from a live CD but (surprise surprise!) the volume doesn't even show up as it normally does and so cannot be mounted. If I try to mount it "manually", with

```
sudo mount /dev/sda5
```

I get

```
mount: can't find /dev/sda5 in /etc/fstab or /etc/mtab
```

and indeed the partition isn't there.

BUT a "sudo fdisk -l" shows the damn partition:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda3               1       19457   156288321    f  W95 Ext'd (LBA)
/dev/sda5   *           1       18893   151757959+  83  Linux
/dev/sda6           18894       19457     4530298+  82  Linux swap / Solaris
```

Gparted "sees" the partition, but says that it's "impossible to mount Volume 155G - The enclosing drive for the volume is locked."

Nothing similar ever happened to me before after an upgrading, even to a beta version. 

I've already posted my problem on several forums, I hope in this one (which is the biggest, isn't it?) I'll find someone who comes up with some help or suggestions. 

Thanks in advance.

---

### Post by clafa on 2010-04-15
+1

Have u tried to remove 'quiet splash' on selected kernel in grub? (it didn't help for me though)

---

### Post by Spaced on 2010-04-15
Yes, I tried that solution but it didn't fix the problem. In the meantime I've worked a lot on my laptop and I've concluded that it was a "hardware" problem: there were some bad sectors in the first part of my hard disk, and some files could not be read. It happened to me also with a clean install, and in some cases I could not even install Ubuntu.
Re-formatting the partition excluding 2Gb at the beginning of the hd has solved. As a confirmation of that, now the disk utility doesn't show "many bad sectors - replace the disk" any longer (it used to do that).
Thanks anyway for your help,

Mattia

---

