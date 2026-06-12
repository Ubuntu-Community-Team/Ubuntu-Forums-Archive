---
title: "Triple Boot 7, Ubuntu and FreeBSD"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by Volmaniac11 on 2010-02-12
Hey, I'm trying to install three different operating systems on my computer.  For now I'm stuck using windows due to certain software that won't work on anything else.  I've used ubuntu on and off for the past few years with varying success.  I am also interested in BSD and have taken a liking to FreeBSD.

Windows is currently installed on my 500Gb HDD but I'm having a problem with the installation of the other two.  It appears that when I try to set the partitions in setup they don't find the other so I end up accidentaly removing the other completely.  Any help would be much appreciated.

Oh, btw.  I would still like to use grub to boot.

Thanks.

---

### Post by Mark Phelps on 2010-02-12
You're using "other" a lot, so it's really hard to figure out what's going wrong ... but you would do best NOT using any Linux utilities to shrink your Win7 partition -- if that's what you're trying to do.

Better to boot into Win7, run the Disk Management utility, and use it to shrink the Win7 OS partition to make room for the other OSs.  After that, boot back into Win7 and try it out to make sure it still works OK with the smaller partition.

---

### Post by kansasnoob on 2010-02-12
> **Volmaniac11 said:**
> Hey, I'm trying to install three different operating systems on my computer.  For now I'm stuck using windows due to certain software that won't work on anything else.  I've used ubuntu on and off for the past few years with varying success.  I am also interested in BSD and have taken a liking to FreeBSD.

Windows is currently installed on my 500Gb HDD but I'm having a problem with the installation of the other two.  It appears that when I try to set the partitions in setup they don't find the other so I end up accidentaly removing the other completely.  Any help would be much appreciated.

Oh, btw.  I would still like to use grub to boot.

Thanks.

That's kind of "sketchy" info. Are you trying to install FreeBSD and Ubuntu on a different drive than Windows?

Same drive as Windows?

How many drives in total?

---

### Post by Volmaniac11 on 2010-02-12
Ok, sorry i wasn't specific enough.  I have one single 500Gb HDD. Currently windows is only installed on 350 of the Drive, with the rest unpartitioned.  Windows seven does not need to be shrunk, but I instead have an issue utilizing the rest of the space.  From there I can install linux, but when installing bsd the linux partition does not show up on the partitioner.  I'm mostly having a problem with linux or bsd recognizing the other is there and is probably to do with the partition format.

---

### Post by kansasnoob on 2010-02-12
That's very helpful. Could you please boot the Ubuntu Live CD choosing to Try Ubuntu without changes, and from the Live Desktop go to Applications > Accessories > Terminal and run the commands:

```
sudo fdisk -l
```

BTW that's a lower case L.

```
sudo parted /dev/sda print
```

That will give us a pretty fair picture of your partition structure :)

---

