---
title: "/boot too small for Gutsy gibbon"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by pbardet on 2007-11-01
Hi,

I curently have a separate /boot partition which is too small (62Mb) while the updater requests 62.7Mb of free space. It is an ext2 filesystem while my / file system is reiserfs.

I would like to move the /boot directory and its  content to my / partition and remove /boot from my fstab, but I know there is a limit where the boot files have to be to be found by the bootloader. I'm also not sure if grub would be able to boot from a reiserfs partition.

Or should I reinstall from scratch ? :(

---

### Post by ddrichardson on 2007-11-01
I think you are referring to the 1024th cylinder limit, which actually doesn't effect either Reiser or Ext2. In fact I haven't come across a BIOS that has that limitation in a long time. But back up of course - I could be wrong.

---

### Post by Pumalite on 2007-11-01
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

---

### Post by logos34 on 2007-11-01
> **pbardet said:**
> I would like to move the /boot directory and its  content to my / partition and remove /boot from my fstab, but I know there is a limit where the boot files have to be to be found by the bootloader. I'm also not sure if grub would be able to boot from a reiserfs partition.(

Reiserfs is supported.

It might actually be faster to shrink whatever partition is contiguous to /boot and expand the latter into the freed space using the [gparted live cd]("http://gparted.sourceforge.net/livecd.php").

To move /boot to root try this guide, just reverse it:
[http://tekguru.wordpress.com/2007/09/04/howto-moving-boot-to-its-own-partition/](http://tekguru.wordpress.com/2007/09/04/howto-moving-boot-to-its-own-partition/)

---

### Post by pbardet on 2007-11-01
Unfortunately, swap space is next to the /boot partition and I really don't want to remove some of it. But I should be able to follow the guide you sent me (I have a pretty good idea how to do it anyway, I was just unsure about reiserfs support).

Thanks. I hope this will allow me to move to Gutsy Gibbon without too many problems.

---

### Post by Oxydius on 2007-11-03
You may delete or move previous kernels somewhere else in order to do your upgrade.

For example :

```
mkdir /tmp/kernels
mv /boot/*2.6.* /tmp/kernels/
```

then update; your /boot should have sufficient free space, and the update will install a new kernel in there anyway. Don't forget to recover your kernel from /tmp/kernels in case something goes wrong.

If your /boot remains too small, as has happened to me before, you may mount a tmpfs on top of /boot to do the upgrade process, then recopy the files to your real boot partition.

---

### Post by pbardet on 2007-11-07
The move worked fine, even though I screwed up my paths at some point (forgot to add /boot to all kernel lists in menu.lst) but I was able to edit the boot menu when grub did not find the kernel. Great feature of grub :)

Since I fixed that issue, the upgrade seems to work fine (it's still running currently since it stops every half hour to ask a question about one of the packages). I hope it will be finished tonight when I get home, unless there's one more question to answer in the middle of the process...

---

### Post by pbardet on 2007-11-07
Spoke too fast.
While cleanng up, the upgrade crapped out. I had to manually finish the upgrade by running the dist-upgrade command, after cleaning up the database lock.
Then, while rebooting, I found out grub was not updated properly (wrong pathes/hd usage). This was "easy" to correct though.

Now, I can't run any command that uses kdesudo. For some reason, I get the message: "command not found" when I select anything requiring super user privilege, from the kdemenu. I tried to remove my existing kde config files, but no change.

I'm not sure if I have to reinstall from scratch, or try to fix the issue.:(

---

### Post by pbardet on 2008-02-06
When I updated the kernel yesterday, I found out that my menu.lst got regenerated and the /boot I added in all my paths were gone.

After looking into the issue, I found out that the update uses a script update-grub to regenerate the menu.lst and uses some parameters directly in menu.lst. I can't find a way to let update-grub know that it needs to add /boot in front of all my kernel/initrd ines.

I don't really want to update the file by hand after each update. I'm pretty sure there is a way to do it, since when I installed my mythubuntu box with only one partition for everything (default install), the menu.lst is properly generated with /boot path. It looks like update-grub keeps some info that was generated during initial install and that I can't get rid of it when moving things.

---

### Post by pbardet on 2008-02-06
Looks like I will have to look at the kernel-img.conf file tonight. It may solve my issue.
I will post back when I figure it out. Looks like I'm not the only one to have issues with update-grub when kernels are updated.

---

