---
title: "Please help, I think I deleted everything."
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by MoistureMan on 2010-09-29
I'm not sure if this is in the right category, so sorry in advance.

I just attempted to install Ubuntu 10.10 and dual-boot it with Windows XP. I "installed" it from a live cd, from which I'm writing this. In the partitioning stage of the installation I was asked if I wanted to unmount partitions in /dev/sda and I can't recall what I chose. I think that's critical. Then I was given three options, one was to install the mside by side. I chose that one, and then was given a window that only showed Ubuntu, and said it would have 94 bytes or something like that. And then the evil god Loki took over me and made press install now. May I comment now that having several installation windows display "install now", and making one guess if the next one is another option window or the actual installation makes for such terrifying adventures. 

Anyway, there was a window asking where I live whilst a bar was filling up below. I think it said it was for the swap partition. That one filled up, then another started, and I logged out before it finished. It barely started, I think. 

Then I rebooted and nothing came up, and when I looked at the partitions from the live CD I saw that all the drive is in ext4. I think I deleted everything. I opened up the 250GB File-system folder and all it has is a 30G folder called lost+found which I can't access.

So what I'm getting at is... Did I delete everything? There are some important files (namely pictures) in this drive and if they're salvageable I might stop hitting myself repeatedly. 

Please help.

---

### Post by CandidMan on 2010-09-29
Don't know how much help I can be, but I'll start by trying to clarify some of the things you mentioned

1. Did you actually interrupt the install. From what I recall time and location settings are made early on during installation(for 9.10 at least)

2. You restarted and absolutely nothing came up?

3. 94 bytes sounds awfully small for a operating system

I've got a feeling there's no quick and easy fix for this. If your drive is properly formatted then I think all the data was overwritten

P.S. I'm no computer expert but I heard good things about [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk_Livecd") about the time my Windows partition was 'lost'

---

### Post by MoistureMan on 2010-09-29
1. I interrupted it by logging out. Strangely it seems like it let me change location settings while it worked on the partitions.
2. There was a "_" sign blinking, which I think is the one for the program that lets you choose an operating system. It never went past the blinking.
3. I have no idea. I think it might be because I chose "no" to unmounting the drive.

I'm feeling like I'm fairly screwed myself. If anything, if there could be data in that lost+found folder, how can I access it?

Thanks for the reply.

---

### Post by CandidMan on 2010-09-29
Alt+F2, then type gksudo nautilus

But Lost+Found isn't quite what you think and I don't it'll make any difference with a live CD

---

### Post by MoistureMan on 2010-09-29
Well, I ran your command and it opened up a folder containing an empty folder, so no luck there. Just to make sure I'm understood, the lost+found folder is in the 244GB Filesystem folder, not in my linux partition, I think (too much).

Again, thanks. I guess I'll wait a couple hours for another reply and format the damn thing.

---

### Post by CandidMan on 2010-09-29
If you've got a 'Lost +found' on the hard drive it looks like Ubuntu' installed some of the way, which means besides formatting, some data's been written to the hard drive

And if I'm not mistaken(someone let me know if I am) you're hard rive will partitioned /dev/sda, sda2, sda3 and so on.

If you can see multiples it's likely you didn't overwrite the whole thing

Besides Testdisk, I also hear [Knoppix]("http://www.knoppix.net/") used to troubleshoot problems like this

In the meantime, try and enjoy Ubuntu :-|

Not the best introduction I know

P.P.S. [http://serverfault.com/questions/163416/can-i-unformat-an-ntfs-volume-that-was-formatted-as-ext4](http://serverfault.com/questions/163416/can-i-unformat-an-ntfs-volume-that-was-formatted-as-ext4)

---

### Post by MoistureMan on 2010-09-29
Can I even download Knoppix in the live cd? I don't have access to a different computer.

Edit: And yes, not the greatest introduction, but I guess I sort of knew it was coming. It doesn't help the panic attack I'm fending off currently, though.

---

### Post by mattgyver83 on 2010-09-29
I think the easiest way to determine if you deleted windows and the disk without going through too much trouble is probably to do the following;

> 1.  Boot into the Ubuntu Live CD and run the 'try ubuntu without installing' option.

2.  When you get into Ubuntu go to System > Administration > Gparted.  If it asks you to apply any changes ever say no.

3.  In the top right is a dropdown menu where you can select from available drives.  If you have 2 drives they will be listed like /dev/sda and /dev/sdb (could be /dev/hda also).

4.  Select the first drive from the list and look at the partition table layout (bar) it displays about the disk information.  To determine the possibility of Windows existence, you are looking to see if any of those partitions are labeled as an NTFS partition in the filesystem column ( i believe outlined green).

Repeat this check for the next drive in the dropdown until you have verified all disks.

If you don't see an NTFS partition (and have only one drive) than its pretty clear that you overwrote your Windows filesystem and those files would have been destroyed in the Format/Filesystem creation/Install process.

Report back your findings because its possible you could have multiple ntfs partitions and if that is the case you could attempt to mount them to look through the filesystem to see if its the data you need.

---

### Post by MoistureMan on 2010-09-29
I'm afraid there's not such NTFS partition. Thanks for the help, I'll format the drive now.

---

### Post by Serpher on 2010-09-29
I know this sounds rediculous, but get an external hardrive with at least as much free space on it as your hardrive, and type the following commands:

```
fdisk /dev/sda
d (Delete)
n (new)
1 (Partition 1)
<Press Enter to start at default cylinder>
<Press Enter to end at default cylinder>
w (write and quit)
```

This will prepare your drive to extract raw binary data. After you do that, locate your external hardrive under /dev/ by using 'ls /dev/|sd*'
There should be something like sdc1 or sdb1. Mount it and extract the data using:

```
mount -t vfat /mnt/
strings /dev/hda1 > /mnt/extraction
```

The final command will probably take quite a while, hours even. When it's done open the file /mnt/extracion in gedit (Text Editor) and browse through it looking for headers of data and such. By using the pointers at the end of blocks and studying the headings of the blocks will allow you to figure out what's what. If you say a jpeg, copy paste all of the non-header/footer info into a blank document with the extension.jpg. I don't suggest doing this unless your data is extreamly important to you, as when I did it on my USB it took a while and it was only 8G.

---

