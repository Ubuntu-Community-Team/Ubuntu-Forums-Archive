---
title: "Ubuntu boot error"
date: 2012-11-07
forum: Installation &amp; Upgrades
---

### Post by WestChi on 2012-11-07
I installed 12.04 LTS from a USB and had no issues with the install for a week or so with numerous restarts.  I installed Amahi, Greyhole, SABNZBd and crashplan.  During the copying over of my files from my WHS to my new Ubuntu Greyhole File Server, I maxed out the boot drive.  I used a live CD to delete some of the copied files and create enough free space to boot the OS.  Ever since that I have had issues and now it will not boot at all.

I tried Boot-repair recommended repair
Advanced options Boot-Repair
tried Noacpi etc. options
ensured the correct drive was selected in the BIOS to boot.
GParted to ensure the partition was at the beginning of the drive (Only one partition on the drive)

I am lost now and not sure what to do.

I either get the "Gave up waiting for root device" error or the blank screen with blinking underscore.

This is from boot-repair:
[http://paste.ubuntu.com/1341589/](http://paste.ubuntu.com/1341589/)

Thanks in advance

---

### Post by Rubi1200 on 2012-11-09
Hi and welcome to the forums :-)

Calling on some others to offer advice here.

Thanks.

---

### Post by oldfred on 2012-11-09
Not familar with Greyhole. Lots of drives. :)

Several issues, not sure if they relate to booting. 

The one that may relate to booting:

```

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  76.139915466 = 81.754611712   boot/grub/core.img                             1
  76.135406494 = 81.749770240   boot/grub/grub.cfg                             1
   2.631397247 = 2.825441280    boot/initrd.img-3.2.0-29-generic               2
 464.506397247 = [COLOR=Red]498.759946240[/COLOR]  boot/initrd.img-3.2.0-32-generic               2
  76.134498596 = 81.748795392   boot/vmlinuz-3.2.0-29-generic                  1
   2.544666290 = 2.732314624    boot/vmlinuz-3.2.0-32-generic                  1
   2.631397247 = 2.825441280    initrd.img.old                                 2
   2.544666290 = 2.732314624    vmlinuz                                        1
  76.134498596 = 81.748795392   vmlinuz.old                                    1
```

We have seen where some BIOS have issues with either grub or boot files that are far apart on drive. Boot-Repair suggests a separte /boot. I usually suggest a smaller / (root) or 25GB or thereabouts and separate /home or data partitions. 

You also have this:

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.
```

But sde looks like it is MBR. Was drive gpt before? Windows will convert gpt drives to MBR but only overwrite the primary partition table leaving the backup. Linux sees the backup & MBR partitions and gets confused. Best to remove extraneous backup gpt partition table. This could cause issues on a lot of things as any script that scans drives including grub booting may see error and stop.

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sde > parts_sde.txt

Are you booting from sdb in BIOS?

Not seen the fstab with /var/hda/drives, is that something from Greyhole?

Also this which may need some housecleaning.
```

 Duplicate sources.list entry cdrom:.....
```

sudo cp /etc/apt/sources.list ~/sources.list.backup
Then edit sources.list

---

