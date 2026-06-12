---
title: "Permissions when mounting drives via fstab"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by bsprowl on 2007-02-17
I cannot write to any of the disks I added to fstab.  Here's the fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=ffe54f79-35cc-472c-a5bd-f6b107eed738 /boot           ext3    defaults        0       2
# /dev/hda5
UUID=d9639c2a-1dd1-46b2-abfc-c19e656cc0d0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
# mount the SATA drives
/dev/sba1 /media/windows/sata1 vfat defaults,umask=000 0 0
/dev/sba2 /media/windows/sata2 vfat defaults,umask=111 0 0
/dev/sba3 /media/windows/sata3 vfat defaults,umask=022 0 0
/dev/sba4 /media/windows/sata4 vfat defaults,noexec 0 0
# mount the Windows 2K drive
/dev/hdb1 /media/windows/win2k vfat defaults 0 0

As you can see I've tried several different combinations of options to allow the user to use the drives (read-write access.)  I then opened the text editor and tried to save a short text file to each of those disks.  The result was the same for each - "You do not have the permissions necessary to save the file."

One of those methods for mounting a drive should let me have complete access to a drive.  However, none of them worked. I got the same error for each drive.  

Thanks in advance,

Bob

---

### Post by kidders on 2007-02-17
Hi there,

> **bsprowl said:**
> 
/dev/sba1 /media/windows/sata1 vfat defaults,umask=000 0 0
/dev/sba2 /media/windows/sata2 vfat defaults,umask=111 0 0
/dev/sba3 /media/windows/sata3 vfat defaults,umask=022 0 0
/dev/sba4 /media/windows/sata4 vfat defaults,noexec 0 0


Should these be /dev/s**d**a instead of /dev/s**b**a? (Basically I'm wondering whether your /etc/fstab settings are being applied at all.)

---

### Post by bsprowl on 2007-02-17
Duuuhhhh...  I'll bet your right. Ran fdisk -lu and it shows the drives as /dev/sda1 ... /dev/sda4

Thanks I post again when I've tried your "fix".

Bob

---

### Post by bsprowl on 2007-02-17
Your fixed worked - of course. 

But only for the sata1 partition.  

None of the other "permissions" worked giving the original error.

I was fully expected the sata4 and win2k partitions to be writeable as well with the permissions I used.  

I want to make them all read-write (noexec) by anyone with ability to make directories and files.  I thought "umask=111" would do that.

Bob

---

### Post by kidders on 2007-02-17
> **bsprowl said:**
> I want to make them all read-write (noexec) by anyone with ability to make directories and files.  I thought "umask=111" would do that.

You could try something like **noexec,fmask=111,dmask=000**. Technically, directories need their execute bits set in order to be traversable. (The ability to read directory contents is controlled by the read bits.)

---

### Post by bsprowl on 2007-02-17
I never heard of dmask and fmask and trhey aren't in the books I have "Running Linux" and "Linux ina Nutshell".

I just did a search and found some references that said they were for remote disks.  Will they work on local drives?  

Bob

---

### Post by kidders on 2007-02-17
Hey again,

> **bsprowl said:**
> I never heard of dmask and fmaskYou can find a description of them on **mount**'s man page (which is quite long), in the **Mount options for fat** section. I figured it would be a neat way of allowing you to have directories appear "chmod ugo+x" without having to do the same to your files.

> **bsprowl said:**
> Will they work on local drives?I imagine so. Having said that, I don't use FAT filesystems ... all the same, I'd be suprised if the man page is wrong.

---

### Post by geovino on 2007-02-18
> **bsprowl said:**
> Duuuhhhh...  I'll bet your right. Ran fdisk -lu and it shows the drives as /dev/sda1 ... /dev/sda4

Thanks I post again when I've tried your "fix".

Bob

I ran $ fdisk -lu and nothing came up. Is that the correct command for showing your drives and partitions?

---

### Post by bsprowl on 2007-02-18
gevino:  actually I ran "sudo fdisk -lu"; sudo is needed to allow you to provide your password.

I'll read the manual for mount...I read it for chmod but not mount.

Thanks,

Bob

---

