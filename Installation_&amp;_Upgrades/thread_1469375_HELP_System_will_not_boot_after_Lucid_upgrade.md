---
title: "HELP: System will not boot after Lucid upgrade"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by chrestomanci on 2010-05-02
I have an AMD64 system, which I recently upgraded to Lucid 10.04. The system now fails to boot after the upgrade. Recovery mode makes no difference.

When I attempt to boot, I get a series of messages about file systems needing checking, and also some messages from ureadahead-other. (process terminated status 4), though a post here says that status 4 is in fact not an error.

I have sucessfully booted the Lucid desktop install CD in live CD mode, mounted the filesystems, and started parts of my system in a chroot. In that system I tried running an update, and removing plymouth, but it made no difference.

Do you have any other suggestions on how I can get my system working.

I did take a backup of /etc before I upgraded, so I could get back to a karmic install, but the pain in doing so would be considerable, so I would prefer to avoid that if possible.

---

### Post by kkady32 on 2010-05-02
hi,i have the same problem,after upgrade or after fresh install.

---

### Post by chrestomanci on 2010-05-02
I have got my system back.

The problem was that mountall was choking over the following entry in /etc/fstab:

```

# Make the USB bus accessible to virtual box VMs
none    /proc/bus/usb    usbfs    devgid=130,devmode=666    0    0

```

The problem is that /proc/bus/usb no longer exists in Ubuntu 10.04. Once I commented out that line, the system booted fine.

When I searched for the line, I can see that other Virtual Box users have experienced the same issue from the opposite direction:

[http://ubuntuforums.org/showthread.php?t=1445314](http://ubuntuforums.org/showthread.php?t=1445314)

---

### Post by kkady32 on 2010-05-03
that is /etc/fstab:



# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=aef8c144-198d-46b7-b769-e48e998cd599 /               ext4    errors=remoun$
# swap was on /dev/sda5 during installation
UUID=eb3e6af6-b1b3-475b-a8f2-5ba814bfb55f none            swap    sw           $
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by chrestomanci on 2010-05-03
> **kkady32 said:**
> that is /etc/fstab:
```

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

I suggest you comment out the entry for the floppy drive, as presumably you don't normally have a floppy in the drive when you boot.

You could also try putting a formatted floppy disc in the drive during bootup and see if it make any difference.

---

### Post by kkady32 on 2010-05-03
tx,i solved my problem too ago few minutes,to me was from video driver.
cheers

---

