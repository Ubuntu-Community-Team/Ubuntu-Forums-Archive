---
title: "Getting 'insert boot media' error after installation 9.10"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by loop2kil on 2009-11-15
installation seems to go very well...I've tried installing direct from the disk as well as from the live cd with the same result. 'reboot and select proper boot device or insert boot media blah blah.''

I have double and triple checked the bios boot order and all is well.

Boot device is an LSI SAS3442E-R raid controller, is there something i need to do specifically to get things rolling?  Is there something in the MBR i need to change since it had winxp 64 bit on previously?

---

### Post by ricardo.gloe on 2009-11-15
Boot from the Live CD, and have a look at /etc/fstab (in the root partition).
 
Post the results.

---

### Post by loop2kil on 2009-11-15
not seeing the fstab in the etc folder...i did a search for fstab and found lots of hits but not sure which one is what your asking for.

---

### Post by loop2kil on 2009-11-15
I found the most appropriate text file of fstab:


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=fa67771d-5bad-4389-8d3d-fd4624d90ec8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=dac92a95-9835-4dd7-9d56-8541285b87df none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by loop2kil on 2009-11-15
# /etc/fstab: static file system information.
#
# The following is an example. Please see fstab(5) for further details.
# Please refer to mount(1) for a complete description of mount options.
#
# Format:
#  <file system>         <mount point>   <type>  <options>    <dump>    <pass>
#
# dump(8) uses the <dump> field to determine which file systems need
# to be dumped. fsck(8) uses the <pass> column to determine which file
# systems need to be checked--the root file system should have a 1 in
# this field, other file systems a 2, and any file systems that should
# not be checked (such as MS-DOS or NFS file systems) a 0.
#
# The `sw' option indicates that the swap partition is to be activated
# with `swapon -a'.
/dev/hda2    none        swap    sw                0 0

# The `bsdgroups' option indicates that the file system is to be mounted
# with BSD semantics (files inherit the group ownership of the directory
# in which they live). `ro' can be used to mount a file system read-only.
/dev/hda3    /        ext2    defaults            0 1
/dev/hda5    /home        ext2    defaults            0 2
/dev/hda6    /var        ext2    defaults            0 2
/dev/hda7    /usr        ext2    defaults,ro            0 2
/dev/hda8    /usr/local    ext2    defaults,bsdgroups        0 2

# The `noauto' option indicates that the file system should not be mounted
# with `mount -a'. `user' indicates that normal users are allowed to mount
# the file system.
/dev/cdrom    /cdrom        iso9660    defaults,noauto,ro,user        0 0
/dev/fd0    /floppy        minix    defaults,noauto,user        0 0
/dev/fd1    /floppy        minix    defaults,noauto,user        0 0

# NFS file systems:
server:/export/usr    /usr    nfs    defaults            0 0

# proc file system:
proc        /proc        proc    defaults            0 0

---

### Post by loop2kil on 2009-11-15
one thing to note...I did see under 'Disk Utility' where the main drive was not showing 'bootable'...on my last live cd attempt I tried making it bootable after the installation and it said the operation system had an error.

[http://s240.photobucket.com/albums/ff210/loop2kil/?action=view&current=Screenshot-1.png](http://s240.photobucket.com/albums/ff210/loop2kil/?action=view&current=Screenshot-1.png)
[IMG]http://s240.photobucket.com/albums/ff210/loop2kil/?action=view&current=Screenshot-1.png[/IMG]

---

### Post by ricardo.gloe on 2009-11-15
Have you checked the cd for defects? and checked the md5 sum of you your downloaded source/cd?

I guess it's possible for an error to occur which allows a complete installation but prevents a functional OS.

---

### Post by loop2kil on 2009-11-15
> **ricardo.gloe said:**
> Have you checked the cd for defects? and checked the md5 sum of you your downloaded source/cd?

I guess it's possible for an error to occur which allows a complete installation but prevents a functional OS.

checked the disk and there were no errors...redownloading again on another computer and will do the m5checksum on it.

---

### Post by loop2kil on 2009-11-16
I feel like my issue still exists within the MBR...

I'm trying to repair/install grub but get stuck here...I don't know what my root and boot should be.  Sorry I'm still a newb.


[http://s240.photobucket.com/albums/ff210/loop2kil/?action=view&current=Screenshot-1-1.png](http://s240.photobucket.com/albums/ff210/loop2kil/?action=view&current=Screenshot-1-1.png)

[IMG]http://s240.photobucket.com/albums/ff210/loop2kil/?action=view&current=Screenshot-1-1.png[/IMG]

---

### Post by ricardo.gloe on 2009-11-16
I think you may have to take a look at, since you're using a raid controller. 

[https://help.ubuntu.com/community/Installation#Installing](https://help.ubuntu.com/community/Installation#Installing) on external or RAID hard disks

---

### Post by ricardo.gloe on 2009-11-16
This article seems more informed and easier to understand.

It seems you'll have to do some reading and preparing for this to work on your current hardware setup. I suggest you format the drives and run a clean install following the steps in the article. Backup data on separate (unused) disks or partitions.



[https://help.ubuntu.com/community/Installation/SoftwareRAID?action=fullsearch&context=180&value=Convert+to+software+raid&titlesearch=Titles](https://help.ubuntu.com/community/Installation/SoftwareRAID?action=fullsearch&context=180&value=Convert+to+software+raid&titlesearch=Titles)

---

### Post by Gigastorm123 on 2010-04-30
a few minits ago i just experenced the same problem, and though i know this isnt the propper solution i turned it on and off about twelve times and on the 12th tim it worked fine but thats just my results i dont know what others may experience

---

