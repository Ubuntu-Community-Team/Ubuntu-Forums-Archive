---
title: "Dapper-&gt; Edgy: Upgrade Hangs on Reboot"
date: 2007-09-24
forum: Installation &amp; Upgrades
---

### Post by wacole on 2007-09-24
I'm trying to upgrade from Dapper to Edgy.  I followed the recommended method on the forum, however, after the upgrade completed and I rebooted, loading stalls/hangs.  So I dropped to the Grub menu and selected *Ubuntu, kernel 2.6.15-29-386 (recovery mode)*, then restarted.  Boot progressed until a hang at:

*Begin: waiting for root file system ... ...*

[Approx 4 min wait]

[I]Done.
ALERT! /dev/hda1 does not exist.  Dropping to shell!

BusyBox v.1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty: job control turned off[/I]
*(initramfs)* 

I tried *mount /dev/hda1* which yielded: 
*mount: Cannot read /etc/fstab: No such file or directory.*
[OK, I'm in RAM and there is no fstab on the /etc subdirectory.]

Is there a command from BusyBox that will tell me which drives are mounted?  I'm booting from a PATA drive on what should be hda1, but, obviously, isn't.  I'd be grateful for any guidance.

Thank you very much, indeed.

---

### Post by Seisen on 2007-09-24
Do you have an option to boot into the edgy kernels at all, they should be 2.6.17.xx. If that doesn't work you can chroot into Ubuntu with a live-cd and fix it that way.

---

### Post by PhantomWA3 on 2007-09-24
I am having the same problem, how would you fix this once you have booted up? I can now boot up using a generic kernel (Fiesty) so can edit the files.  For more detail on problem see my post:

[http://ubuntuforums.org/showthread.php?t=558614]("http://ubuntuforums.org/showthread.php?t=558614")

Thanks.

---

### Post by Seisen on 2007-09-24
> **PhantomWA3 said:**
> I am having the same problem, how would you fix this once you have booted up? I can now boot up using a generic kernel (Fiesty) so can edit the files.  For more detail on problem see my post:

[http://ubuntuforums.org/showthread.php?t=558614]("http://ubuntuforums.org/showthread.php?t=558614")

Thanks.

If you have internet access then do a ```
sudo apt-get update 
sudo apt-get upgrade
``` and see if their are any more updates that might not of installed.

---

### Post by PhantomWA3 on 2007-09-24
No new updates where found.

Thanks,

Phantom

---

### Post by Seisen on 2007-09-24
Also try ```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by PhantomWA3 on 2007-09-24
Nope nothing.

This is the error I get:

```
Check root=bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/hda1 does not exist.  Dropping to a shell!
```

and If i boot up using the generic kernel and run fdisk -l  I get the following:

```
Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       30024   241167748+  83  Linux
/dev/hda2           30025       30401     3028252+   5  Extended
/dev/hda5           30025       30401     3028221   82  Linux swap / Solaris
```

So hda1 does exist so I cant understand why it fails to boot.

Thanks,

Phantom

---

### Post by wacole on 2007-09-24
Re: available kernels; I only see 2.6.15-xxxx, no 17s, so maybe Edgy didn't upgrade after all.  Would it be wise to boot from an Edgy LiveCD and then try to reinstall over what's already on  /dev/hda1?

Thanks,

---

