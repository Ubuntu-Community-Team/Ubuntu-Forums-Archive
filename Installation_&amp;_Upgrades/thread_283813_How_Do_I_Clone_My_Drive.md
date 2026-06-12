---
title: "How Do I Clone My Drive"
date: 2006-10-24
forum: Installation &amp; Upgrades
---

### Post by Keymaster on 2006-10-24
I have a seagate hdd in my Ubuntu 6.06 system, and I don't trust seagate drives, so I would like to switch it with a Western Digital drive.  How do I make a complete image of the drive (including grub, and partitions) for my linux installation?  This is my server, and I can't spend time reconfiguring it, and reinstalling linux, so a drive image would be the best choice.  It is an ext3fs, and I need to preserve all settings, files, folders, and file permissions.  This is VERY important to me, and I must be able to do this soon.  I believe the drive is a SATA drive, but it might be IDE, so if the directions/software you know of supports one, or the other, please note which.  I need software that requires very little knowledge to use, since I don't have time to learn it, and the software should also be able to put the image on a drive that is not partitioned (ie. it also images the MBR, and partition table)  Thanks

---

### Post by wkulecz on 2006-10-24
IMHO the fastest way will be to get the Knoppix 5.01 DVD, boot it, and use partimage after installing the new drive.  As long as all the new partitions are the same size or larger as the originals it should go smootly.

Don't forget to backup and restore the boot loader to the new drive.

Having Knoppix is a great tool to recover should something go amiss.

I don't understand why you don't "trust" Seagate drives.  They have a 5 year warrenty, everyone else is lucky to give you 3 years unless you buy "enterprise class" high priced product.

If partimage is not doing what you want, I think you'll have to buy Norton's "Ghost"  I think you have to do all partitions and the MBR individually with partimage, whereas Ghost can do an entire disk, but partimage restores and backsup much faster than Ghost, but Ghost can resize on the fly.  I use both. partimage for "clones",  Ghost for moves to a larger drive/partition.

--wally.

---

### Post by Keymaster on 2006-10-24
I would use partimage but I don't have the time, patience to setup the partitions ahead of time, and I believe ghost can't copy GRUB properly.  I believe there is something about the dd command that can do the entire harddisk including the MBR, but IDK how to use it, and google has failed to help.  Any help with dd would be nice.  (dd not D&D lol)

---

### Post by wthanna on 2006-10-24
The easiest way I've found is using a boot disk called G4U (ghost for unix). Connect the hard drive.. boot from G4U... type one command.... wait for process to finish...  you will have two identical drives. 

[www.feyrer.de/g4u/](www.feyrer.de/g4u/)

Nothing is easier.

---

### Post by tkdolphin on 2006-10-24
dd will clone your hard drive. Be careful though, dd can be unforgiving if you clone the wrong hard drive. Another downside to dd is that it takes quite a bit of time to clone the drive.

Here's a link that may help, [http://www.debianhelp.co.uk/ddcommand.htm](http://www.debianhelp.co.uk/ddcommand.htm)

---

### Post by dcstar on 2006-10-25
> **wthanna said:**
> The easiest way I've found is using a boot disk called G4U (ghost for unix). Connect the hard drive.. boot from G4U... type one command.... wait for process to finish...  you will have two identical drives. 

[www.feyrer.de/g4u/](www.feyrer.de/g4u/)

Nothing is easier.

Last night I copied my old 40GB HD to my new 40GB super quiet HD using **Ghost for Linux**, it took about 2 hours to clone the whole drive and everything worked as it did on the new disk (except I can't hear it any more!!).

Go to the [http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l), download the ISO and burn yourself a boot CD.

---

