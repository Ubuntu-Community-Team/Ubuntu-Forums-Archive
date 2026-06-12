---
title: "[ubuntu] bootable backups"
date: 2014-01-14
forum: Installation &amp; Upgrades
---

### Post by irvingdave1 on 2014-01-14
Hi,

I've moved home directories, mail, media, config out to a backed up raid - and am going to have 2 ubuntu installs on SSD (the idea being I can have a latest / dev version along side my more stable version - and only 'flip' for real when everything is stable). I'll have 3 partitions on the SSD - 2 for the installs and 1 for shared 'fast data'.
I have an external drive more than large enough to backup the SSD.

What I'd like to do if possible is somehow set up a full backup of the SSD which I can also boot from: I.e. should I loose my SSD within seconds I can just get right back to (nearly) where I was by booting in to one of the installs on the external drive.

Is this reasonably straightforward to accomplish? Are there tools which automate this? I've looked at a few candidates (e.g. mondorescue) - but just wondering if anyone has any experience doing this - or any links to any guides they'd be prepared to share.

Many thanks in advance,

Dave

---

### Post by maestrobwh1 on 2014-01-14
Easiest with no other tools is to use Clonezilla-live bootable CD/usb

You could also boot using any linux live CD/usb and use the dd command

dd if=/dev/sdx of=/dev/sdy conv=notrunc,noerror

other info [http://serverfault.com/questions/4906/using-dd-for-disk-cloning](http://serverfault.com/questions/4906/using-dd-for-disk-cloning)

Or, you can install dump, but this is a bit more tricky for anyone who is not a somewhat advanced user (I am far from being an expert, perhaps I am an advanced novice). The target disk can also be smaller, as long as the data actually fits. I prefer it but one has to install grub to the target disk and change some uuid references in the target disk's /boot/grub/grub.cfg and /etc/fstab.  

The thing I like is that you can do this all from your running system (don't be using applications or do something odd like update packages during the "dump."  

```
dump 0f - / | (cd /mountpoint/targetdisk ; restore -rf - )
```
when completed:
```
grub-install --force --no-floppy --boot-directory=/mountpoint/targetdisk/boot /dev/sdx 
``` 
x is the designation of the target disk. (i.e. sdb)  Do not use a partition number!  
This is for 13.10.  The syntax is different for previous grub versions

Then
```
sudo blkid -c /dev/null
``` 

copy the UUID of the targetdisk to the clipboard in termainl

The easiest thing to do next is to use gedit as root, open up /boot/grub/grub.cfg ON YOUR TARGET DISK and search and replace all references of the root uuid with the uuid of the target disk.

Do the same for /etc/fstab ON THE TARGET DISK.

It 'should' boot.  The better thing about this compared to cloning is that you can plug it back into your running machine and it will have a different UUID so your OS won't be confused about what disk is mounted.  Duplicate UUID disks can really cause some issues on a running OS.

It you have a swap partition, you'd need to create a new one and change the uuid in /etc/initramfs-tools/conf.d/resume then once booted, run 
```
sudo update-initramfs -u
```

If you want to update your backup, I have found that I have to delete the contents of the backup disk and redo this procedure.  You can probably force dump to update files but I want to make sure I have no issues with my copy.

---

