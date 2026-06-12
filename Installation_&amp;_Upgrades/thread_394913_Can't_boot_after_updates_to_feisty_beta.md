---
title: "Can't boot after updates to feisty beta"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by DJMatty on 2007-03-27
Hi

My install of feisty had been working ok, until I ran the updater last night for 50 or so updates. Restarted the machine and now it won't boot.

Turned off splash and quiet and i can't see any errors appearing, although the text does fly past pretty quick.

If I leave it for ages i get into a busybox thing with an (initramfs) prompt.

The install is on raided drives via dmraid and I had installed the latest nvidia gfx card drivers manually (following instructions on the envy web site), so I was wondering if that could be the problem as initrd and the kernel were rebuilt during the updates...

Being new to this, where should I begin looking for the cause of the problem? Where are the log files kept, and what should I look for initially?

Thanks

Matt

---

### Post by bulldog on 2007-03-27
Try booting the previous kernel to see if that one is ok.
If you can login Feisty your install is not damaged.

Now try to boot the recovery mode from the new kernel update.
If that will work,install linux restricted modules.
```
uname -a
``` wil give you your current kernel something like 2.6.20-13-generic.
To install ```
sudo aptitude install linux-restricted-modules-2.6.20-13-generic
```
Reboot and try the new kernel again.

---

### Post by DJMatty on 2007-03-27
Hi

None of the options in the grub menu will boot, 2.6.20-13 or 2.6.20-12. Recovery mode or not. They all go some way to booting then just stop, no errors that I can see.

Does the info that is shown on boot get stored anywhere so I can see if it has errored further up?

Thanks

Matt

---

### Post by bulldog on 2007-03-27
Is it possible it does a fck check? [file/system checkup]
This can take some time,and you can be easily mistaken and think it hangs.

It's rather strange none of your kernels will boot.

---

### Post by DJMatty on 2007-03-27
I'm not sure, there is nothing obvious on the screen that I can see that it's doing an fsck...

I left it booting for a while and it ended up with a command prompt like this (this isn't exact but near enough):

```
BusyBox v.1.1.3 CDebian1.1.1.3-3ubuntu3) Built in shell (bash) Enter 'help' for a list of commands.

/bin/sh: can't access tty; job control turned off
```

my drives are raided, yet when I enter ```
ls /dev/mapper
``` it only returned 'control'

I had to enter ```
dmraid -ay
``` before I could see the raid drives. Could it be that this is the problem, it can't see the drives after it has got so far booting?

Thanks

Matt

---

### Post by DJMatty on 2007-03-28
I tried this morning some further tests.

I let it boot until i got to the busybox (initramfs) prompt.

I then ran 'dmraid -ay', which mapped the raid partitions

Then hit ctrl-d to continue booting.

This then ran more of the boot, until it got further along and then stopped again.

Is it possible that dmraid has been excluded from the initramfs and kernel when it was updated? If so, can I include it by chrooting to my install from a livecd?

Thanks

Matt

---

