---
title: "Hosed Ubuntu 6.06 by apt-get upgrade"
date: 2007-01-25
forum: Installation &amp; Upgrades
---

### Post by LukeKendall on 2007-01-25
I think my problem was caused by my own false assumptions: namely that a proper
way to upgrade a debian-based system was to do 'apt-get update; apt-get upgrade'.
I just wanted to update my installed and working packages to newer versions (I was
running Ubuntu 6.06).  This was my first major upgrade since July when I installed it,
and the download for the updates were about 400MB.

From some later advice I had, a more correct approach is to do "apt-get dist-upgrade"
(and that of course I should have used "&&" not ";" to separate the commands).

But from a quick look at the forums now it seems like the truly correct way might have
been:

```
gksu "update-manager -c" 
```

Anyway, my actual sad story is this:

I did an "apt-get update; apt-get upgrade" on my Ubuntu 6
system.  Apparently it fiddled with the kernel (I had 2.6.15-26-386
installed and it I think installed 2.6.15-26-686.) 

The next day, I noticed it suggested a reboot.  I had a look at
/boot/grub/menu.lst which had been modified (according to
the modification time), but I couldn't pick the change.  It all
looked good, and I have numerous alternative kernels to fall back to
(little did I know...).

Upon attempting to reboot, I got this message:
```

Uncompressing Linux... Ok, booting the kernel
mdadm: /dev/md0 has been started with two drives.
mdadm: /dev/md1 has been started with two drives.
mount: Mounting /dev/hda7 on /root failed: Device or resource busy
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

```
Obviously if I can't mount /root then it won't be able to mount
/root/dev.  It drops into a shell, and I saw that there's nothing
really mounted (I think it's just an initrd file system).

I can mount /dev/md0 (which is "/") to a temporary mount point and
everything's there.  But I can't boot *any* of my Linux kernels.

This suggests to me that it's not a problem with the kernel, it's a
problem with some critical component needed by all the kernels, in the
root file system.

A google search lead me to
[http://www.linuxquestions.org/questions/showthread.php?t=446745](http://www.linuxquestions.org/questions/showthread.php?t=446745) which
suggests that in April last year udev was broken badly.

Since then I've had some other advice, which I'm about to try to fix the installation up:

> 
In terms of recovering your system, it should be as simple as booting a
live CD. When the prompt appears, do

'live root=/dev/md0' or something similar - I can't remember the exact
syntax offhand - but that will get you booted.

Once you are running, use aptitude and check that all the recommended
packages for the new kernel version are present, including udev.

You can then use 'update-initramfs' and 'update-grub' to regenerate the
initramfs which contains a copy of udev, and *that* should let you boot
properly again.


Unfortunately, I can't find a prompt to enter the above!  If I start using the rescue mode
I quickly get to the point where it asks me to choose a device for the root filesystem,
but it only offers me a choice of partitions *within* my raid arrays.

Any advice?

I confess I'm still a little confused.  When I just want to update from one stable set of
packages to the next, what *kind* of update do I do?  A dist-upgrade?  Should I be using **apt**
or **update-manager**?  If I want to upgrade from one stable *release* to the next, like from 6.06 to 6.10, then I
think I'm supposed to use **update-manager -c**, right?

Regards,

luke

---

### Post by LukeKendall on 2007-01-25
Well, I realised that the F6 option on the live CD allows you to edit the boot options, so I'm underway on the repair.

luke

---

### Post by LukeKendall on 2007-01-25
Well, no, that didn't get me much further.  I chose mirrors, etc., and on the final step it asked me to choose a partition for the root filesystem, and once again offered me only the raw partitions, instead of using /dev/md0 as I'd specified from the root= parameter.

luke

---

### Post by LukeKendall on 2007-01-27
Well, I've temporarily given up on trying to recover that.  Instead, I decided to reinstall from scratch into a spare pair of partitions using the 6.06 CD and setting up raid, and all seemed to go well until the reboot, at which point I get the error:

```

Booting 'Ubuntu, kernel 2.6.15-23-386'

root (hd0,0)
  Filesystem type unknown, partition type 0x7
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/md0 ro quiet splash

Error 17: Cannot mount selected partition

Press any key to continue...

```

I think I'll try download and burning 6.10 and try installing that.  If that fails, I reckon I'll give up on Ubuntu and try some other distro.

luke

---

### Post by LukeKendall on 2007-01-27
Well, I've temporarily given up on trying to recover that.  Instead, I decided to reinstall from scratch into a spare pair of partitions using the 6.06 CD and setting up raid, and all seemed to go well until the reboot, at which point I get the error:

```

Booting 'Ubuntu, kernel 2.6.15-23-386'

root (hd0,0)
  Filesystem type unknown, partition type 0x7
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/md0 ro quiet splash

Error 17: Cannot mount selected partition

Press any key to continue...

```

I think I'll try download and burning 6.10 and try installing that.  If that fails, I reckon I'll give up on Ubuntu and try some other distro.

luke

---

### Post by LukeKendall on 2007-01-27
I've started the install of 6.10.  Having previously set up the RAID arrays, I made the mistake of going into "Create MD device", and then, after the installer reported there were no available partitions to turn into an MD device I left that screen, and that's where the install ended.  It looked like it was in some sort of tight loop.

So I rebooted and started the install again, and this time went into "Configure RAID" but instantly selected the "Finished" option, and the install is now proceeding okay.  If it boots up then I'll continue with Ubuntu, if not I'll try SuSE 10 or FC6 I suppose.

luke

---

### Post by LukeKendall on 2007-01-27
No, that failed too.  Trying to boot from 6.10 just gave the error "Error 17, can't mount partition" and that was all.

Sorry, I'm giving up on Ubuntu and trying some other distro.  I think I'll try SuSE 10.

luke

---

### Post by LukeKendall on 2007-01-27
I realised I should at least try a google search to see if this was a common problem.  Apparently the Ubuntu installer doesn't create a correct grub file - it just blindly assumes that the boot partition will always be (hd0,0).  Since mine was on the 6th partition, I followed the tip at [http://www.debianadmin.com/ubuntu-edgy-upgrade-common-problems-with-solutions.htmlprint/](http://www.debianadmin.com/ubuntu-edgy-upgrade-common-problems-with-solutions.htmlprint/)
and changed my entry to (hd0,5) and pressed b to boot and lo!  I have a Ubuntu system that's now booting.

Yep.  It's looking good.

Now to once again install fetchmail and exim etc. and configure them all, all over again.  At least I have a copy of the old config files stashed away in my home directory so it should be faster this time.

And although no one on the forums offered any help, perhaps this thread will be of use to someone else in the future.

luke

---

