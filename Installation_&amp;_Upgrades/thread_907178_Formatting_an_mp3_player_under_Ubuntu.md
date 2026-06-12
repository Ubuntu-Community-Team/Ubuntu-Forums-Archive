---
title: "Formatting an mp3 player under Ubuntu"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by portach king on 2008-09-01
Hi guys,
Having just received an iAudio 7 16gb this morning I'm anxious to get it set up asap. However, I've read this message on the website: [http://www.cowonglobal.com/zeroboard/view.php?id=B15&page=1&sn1=&divpage=1&bmenu=support&sn=off&ss=on&sc=on&select_arrange=headnum&bmenu=support&desc=asc&no=549&bmenu=support](http://www.cowonglobal.com/zeroboard/view.php?id=B15&page=1&sn1=&divpage=1&bmenu=support&sn=off&ss=on&sc=on&select_arrange=headnum&bmenu=support&desc=asc&no=549&bmenu=support)

Unfortunately, the guide is only in Windows.
Now I'm assuming that by using GParted I will have no issues in actually formatting the player, but it's the setting of the "allocation unit size" that confuses me and is the source of my worries. Can anyone provide me with some information and/or advise? Thank you in advance.

---

### Post by modmadmike on 2008-09-01
Usually you can use the default.

---

### Post by portach king on 2008-09-01
> **modmadmike said:**
> Usually you can use the default.

My pardon, but I found your response a little vague. Could you be clearer about what you mean please?

---

### Post by modmadmike on 2008-09-01
The default for windows is 4kb (kilobytes)

---

### Post by portach king on 2008-09-01
Well as mentioned in the link I posted unless the memory allocation is set to 16k ("16,384 bytes") the transfer speed is effected. Is there a way to check the allocation space under Ubuntu?

---

### Post by manishtech on 2008-09-02
What filesystem are you using the format? fat32 or ntfs?

---

### Post by portach king on 2008-09-02
Preferably, what I'd like to do here is simply format the usb drive in Fat32 with 16k of allocation space.
Someone on the iaudiophile forums came up with a method for doing this in linux, which I've pasted below, but unfortunately I've find it difficult to follow, in particular the first two steps. Maybe someone here could explain this a little clearer?
[QUOTE=sliipy on iaudionet.net]
here follows a short guide for you other linux guys (become root now).

0) plug the device in, wait 5 seconds or so and run dmesg to find out your device name.

1) create a fat32 (lba) partition on your iaudio device (type 0c)
you can use "cfdisk /dev/sdh" (my device is named sdh, this could differ)

2) verify partition layout (just in case)
# fdisk -l /dev/sdh

Disk /dev/sdh: 16.5 GB, 16542334976 bytes
64 heads, 32 sectors/track, 15776 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x00000000

Device Boot Start End Blocks Id System
/dev/sdh1 * 1 15776 16154608 c W95 FAT32 (LBA)

3) create the fat32 filsystem:
# mkfs.vfat -n iaudio7 -s 64 /dev/sdh1
the output you get will just be something like "mkfs.vfat 2.11 (12 Mar 2005)"

4) done! wait a few seconds just in case and then unplug your player... boot it, choose language. plug it back into your computer and mount it (if it doesn't automaticly). now you should see the default folders popping up. and if you run a benchmark or just copy files to it, you should get around 6.5MB/s (!!!)

you can monitor the read/write speed on your device using dstat;
# dstat -dD sdh 5
--dsk/sdh--
read writ
0 6520k
0 6544k
0 6576k[/QUOTE]

---

### Post by portach king on 2008-09-02
Does it make any sense to anyone? :)

---

### Post by manishtech on 2008-09-02
Install Gparted using the command in the terminal

```
sudo apt-get install gparted
```

and then open it and create partitions/format the partiitons.

---

### Post by portach king on 2008-09-03
:)
Thanks but as I said, I uderstand how format the drive (using GParted) but *my one concern* is how do I ensure that there will be an allocated space of 16k of memory when it is finished. I don't want to needlessly format my mp3 player..

---

### Post by portach king on 2008-09-03
Ok, so against my better instinct I decided to format the player using Gparted. The results are as I predicted, no change in the slow transfer speed to the player. Is there anyway of setting that 16k memory allocation, I'd really appreciatte some help on this issue.

---

### Post by portach king on 2008-09-05
*bump*

I hate to have to bump but, please, can anyone help at all??

---

### Post by portach king on 2008-09-06
[IMG]http://www.achildgrowsinbrooklyn.com/photos/uncategorized/2008/04/11/bump_closed.gif[/IMG]

---

