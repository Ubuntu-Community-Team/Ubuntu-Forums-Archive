---
title: "how to automount usb devices by device name instead of uuid"
date: 2013-03-05
forum: Installation &amp; Upgrades
---

### Post by sbalfour on 2013-03-05
After upgrade from 10.10 to 11.10, ugly numbers appear everywhere instead of device names
like sda and hdb.  This is grossly un-user-friendly.  Nobody except device driver and kernel
developers needs to see strings like that.  Consider how unlikely it is to get such a
number transcribed accurately if I have to type it into a terminal on another system, or get
the number over the phone while helping a remote user (I'm a sysadmin).   They're all over
the boot files, too.  1) how do I get USB devices to automount with their device names like
they used to?  2) How do I get those ugly numbers out of the boot files and replaced with
whatever they used to be (presumably things like /dev/sda, etc)?  For reference, I don't
see any such numbers in the Windows boot files or device directories, disk management, etc.

Don't suggest using volume labels... I didn't need them before, and I shouldn't need them now.
And I'd have to put those labels (unique ones, presumably) on dozens to hundreds of disks, 
many of which I don't have direct access to.
                                                                                        Stuart

---

### Post by MAFoElffen on 2013-03-06
This is probably going to get moved from I&U to elsewhere by a mod or admin... As I am trying to figure out how it relates to an Installation or Update. It is more a comment or opinion.

As it relates to sys admin and change management/control... IMHO opinion, you have more control and yet flexibility. You have the option to turn it off in /etc/default/grub for grub2. In that file, you have:
```

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

```
But from the Grub menu and/or CLI, you have the option to use either the UUID, the hdaX or sdX format to mount it. From current Linux, you have the option to use either UUID or sdX formats.

So how does this relate to your title on how to automount devices in Desktop Editions? (Because you know Server Editions have no automount, right?) If it uses "any" kind of scheme in automount, it should be immaterial to the user, as long as it works right?

Since I do sys admin of M$, Linux and UNIX... I'm trying to figure out "if" you are asking anything. I apologize that I can't figure out how your comments fit your title... and I don't see a question or problem there in your post.

---

### Post by sbalfour on 2013-03-06
I uncommented the line you sugested, ran update-grub as root and rebooted. Not a thing changed: there are still UUIDs in /media mount points as well as grub.cfg.
I double checked the timestamps on the grub and grub.cfg files, and they are indeed updated.  Apparently there is an internal option in grub-mkconfig named 
GRUB_DEVICE_IDENTIFICATION that has something to do with the UUID botch up.  Do I need to fix grub-mkconfig.in and rebuild grub itself??  I can, but my issue is,
how do my users get rid of UUIDs?  They're not going to rebuild grub, and a non-standard package on standard servers isn't going to cut it.
                                               Stuart

---

