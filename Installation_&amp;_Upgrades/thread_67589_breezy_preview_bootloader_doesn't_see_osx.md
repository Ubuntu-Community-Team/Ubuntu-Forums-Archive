---
title: "breezy preview bootloader doesn't see osx"
date: 2005-09-20
forum: Installation &amp; Upgrades
---

### Post by tomcogley on 2005-09-20
I know that the grub file needs edited but it does not seem to be there in Breezy.  This isn't a problem in Hoary...the installer sees osx.   This is off the preview cd.   So, the main question is, when it's finally released and i want to upgrade and do it by editing the repositories, will it in some way effect yaboot seeing osx,  and if it did, how in breezy would I edit the boot configuration files, or better yet lock them in in the first place so they could not be changed?
Thanks   TC

---

### Post by tomcogley on 2005-09-20
I suppose I can do this using the partitioner on the install cd to restore grub to see osx?

---

### Post by flange on 2005-09-22
[QUOTE=tomcogley]I know that the grub file needs edited but it does not seem to be there in Breezy.  This isn't a problem in Hoary...the installer sees osx.   This is off the preview cd.   So, the main question is, when it's finally released and i want to upgrade and do it by editing the repositories, will it in some way effect yaboot seeing osx,  and if it did, how in breezy would I edit the boot configuration files, or better yet lock them in in the first place so they could not be changed?
Thanks   TC[/QUOTE]

I had the same problem with a fresh install of Breezy Preview.  Here's how I fixed it:

1.  Find out the partition your OSX install is on.  Look for the partition where is the system = HFS.

```
sudo fdisk -l
```

2.  Edit your /etc/yaboot.conf file.

```
sudo gedit /etc/yaboot.conf
``` 

3.  After the line that starts with "magicboot", add the line "macosx=/dev/hdaX", where X is the number of the HFS partition you found in the first step.

4.  If you want OSX to be the default OS, after the "enablecdboot" line, add the line "default=macosx".

The global section of my /etc/yaboot.conf file looks like this:

[INDENT]boot=/dev/hda2
device=/pci@f4000000/ata-6@d/disk@0:
partition=4
root=/dev/hda4
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
macosx=/dev/hda3
enablecdboot
default=macosx[/INDENT]

5. Save yaboot.conf when you're finished editing.

6. Install yaboot to the bootstrap partition.

```
sudo ybin
```

That's all I had to do to get OSX capable of booting again.  Hope that helps.

---

### Post by flange on 2005-09-22
BTW, can someone please move this to either the Breezy section or the Mac/PowerPC section?  There doesn't seem to be a Breezy/PPC section yet, though that would be the best place for this thread.

Thanks.

---

