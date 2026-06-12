---
title: "Lucid Doesn't Recognise other partitions/USB Drive"
date: 2010-02-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by JCoster on 2010-02-18
For a couple of days now I have been unable to view other partitions on my laptop running Lucid.  I was fine when i upgraded a couple of weeks ago but now under 'Places > Computer' all I see is CDRom and FileSystem, when in fact I should have 2 other partitions.

Similarly, I am no longer able to read my USB pen- nothing happens when I put it in.

Anyone else with the same problem?

I went into 'System > Admin > Disk Utility' but all i get is an emboldened '(null)'.

Cheers!
JC

---

### Post by yelo3 on 2010-02-18
I'm also interesten on fixing this problem

---

### Post by VMC on 2010-02-18
Any changes to fstab?

---

### Post by seeker5528 on 2010-02-18
> **JCoster said:**
> For a couple of days now I have been unable to view other partitions on my laptop running Lucid.  I was fine when i upgraded a couple of weeks ago but now under 'Places > Computer' all I see is CDRom and FileSystem, when in fact I should have 2 other partitions.

Usually I use mountmanager to set up my other partitions, apt-get it or search for it in synaptic.

> Similarly, I am no longer able to read my USB pen- nothing happens when I put it in.

I'm guessing there is something going on between apparmour and libpam-mount, because I get the expected listing in places when I plug in my flash drive, but when I click on it I just get a message indicating permission is denied.

If I install usbmount, it's mounts my flash drive when it is inserted, but at /media/usb0 instead of a mount point that is determined by the way the device identifies its self. Also it is read-only instead of read-write and when I want to unmount the partition on the flash drive it complains that I am not root, so I've been doing that from the command line. 

Later, Seeker

---

### Post by LADmaticCA on 2010-02-18
I was having this problem too. What fixed it for me was re-installing gnome-disk-utility from synaptic, which will also install a package called udisks. After a reboot things were back to normal.

According to synaptic there was an update available to gnome-disk-utility. I guess update manager didn't pick it up.

---

### Post by Ibidem on 2010-02-18
@seeker:
I just figured out some of the usbmount stuff this morning.
/usr/share/doc/usbmount/README.gz
is the documentation; treat it like an ordinary text file, despite being compressed.
Flash drives are automounted as root, with rw only allowed for the user root by default.
What I did to enable using flash drives as an average user was edit /etc/usbmount/usbmount.conf:
FS_MOUNTOPTIONS="-fstype=vfat,utf8,umask=007,gid=46"
where the line read originally:
FS_MOUNTOPTIONS=""
I arrived at those values from comparing my /etc/fstab with the usbmount documentation;
they may be different for you.
Use 
```
cat /etc/fstab|grep gid
#or
cat /etc/fstab|grep vfat|grep gid
#(if you have a vfat partition)
```
to check your own system's defaults.
"-fstype=vfat" means "use the following flags IF the fs is type vfat"

Ibidem

---

### Post by JCoster on 2010-02-19
> **LADmaticCA said:**
> I was having this problem too. What fixed it for me was re-installing gnome-disk-utility from synaptic, which will also install a package called udisks. After a reboot things were back to normal.

According to synaptic there was an update available to gnome-disk-utility. I guess update manager didn't pick it up.

Fantastic- running:
```
sudo apt-get install --reinstall gnome-disk-utility
```
..and then restarting fixed this for me.

Cheers,
JC

---

### Post by yelo3 on 2010-02-19
That works! but my disk does not auto-mount. I always have to go to "computer" and double click on it.

---

