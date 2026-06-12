---
title: "Huge Problem With Windows Partition"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by GameKing505 on 2008-04-25
Ok so I installed hardy heron today and I like what I see, but there's once ridiculously massive problem. I did some reorganization of the partitions on my hard drive, and it all seemed fine, so I installed. Later I wanted to boot into windows (xp) to check if everything was ok, so I did. Of course after resizing the partition I got that message that says there has been a change in my hardware, check is advised, bla bla bla.

I get this whenever I change the partitions in any way, so I figure what the hey, I'll just skip it. So for the first time, I hit a key, and skipped the disk check thingie. Next thing I know windows boots into a splash screen, and that's it. I'm stuck on the "Windows XP Media Center Edition" screen with the blue background. I can move the mouse, but there is no option to log in, change accounts, or any buttons whatsoever. Additionally, I can't access this hard drive from any linux installations I have NO IDEA what is going on except that the error message says that the disk is already in use and adizes me to unmount it through windows or something like that... Anyway, I have all my most important data on that partition, and only like half of it backed up. Is there a way to fix my windows or no? Please I'm desperate!!!!

---

### Post by wshawn on 2008-04-25
First off, Its not that bad.

Boot into Ubuntu and you should be able to get any remaining data pulled to the ubuntu user folder.

More than likely, you changed the number of partitions (not the amount)

Look for the hidden boot.ini in the windows root (C drive)
make a copy of it.

Using sudo fdisk -l or sudo sfdisk -l

List the partitions.

The boot.ini is attempting to load the ntldr pointed to by the boot.ini.  Problem is, its not there.

It used to be, that some Linux installations would shove a /boot partition before the windows one, thereby changing the number of the partition to one higher than before.

A typical boot.ini should look like:

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

You may need to change the 1 to a 2 in both places.  If you changed the bott order of the drives in bios (or grub read it wrong), you can always hit F11, F12 or whatever and force the boot to start directly from the windows partition by passing grub.

If that works then grub is not chain loading as it should.

Just some ideas.

But, by all means backup your data using ubuntu first.

---

