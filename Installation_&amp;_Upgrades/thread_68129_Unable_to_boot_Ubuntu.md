---
title: "Unable to boot Ubuntu"
date: 2005-09-22
forum: Installation &amp; Upgrades
---

### Post by mathias on 2005-09-22
I have problems booting into Ubuntu

I first installed Windows XP on a 10gb partition.
Then I installed Ubuntu on the same disc, but on another 10gb partition (I also created 500mb swap and 500mb Home partitions on the disc.
The rest (19gb) is used by Windows.

After the Ubuntu installation finished, I was logged into it, downloading all the updates to the packages...thinking everything was great...

I then shut down the computer and went to sleep...

Coming home the day after from work, I booted up Windows XP and installed Partition Magic 8 and then converted the second harddrive (which I use for music, documents and such from NTFS to FAT32 to making Ubuntu able to write on it. The convertion gave me an error at 99%, but when I closed down Partition Magic it seemed ok, I could open it and move files, listen to music so on so on...
Then I noticed that the entire first disc had the lable "BAD" on it. It couldn't recognize the different partitions...

I shut down my computer and restarted trying to boot into Ubuntu.
It started to boot and then stopped saying something that there was an Superblock Error and it couldn't mount /dev/hda7.

If I wanted to continue i should press ctrl+D. I did and it continued the startup.
But when I entered my username and password I got this error message:
When I tried to log into the desktop with that account, it gave me a message that said my session was under 10 seconds and it couldn't find user /home/myusername.

Using Acronis disk manager I was able to see the different partitions in XP, so I might be able to format the linux and start the installation over...

Any ideas why this happened and what I can do to solve it???

/Mathias

---

### Post by rcerreto on 2005-09-22
Partition Magic is a great software as long as you have just FAT/NTFS partitions.
Alas, it gave me a lot of problems whenever I had Linux partitions too.
Try using parted (command line) or any gui-flavoured variant (gparted, qtparted, ...)
I don't know whether you'll be able to recover your linux partition, but maybe someone else knows better.

---

### Post by fordfan753 on 2005-09-22
Hmm...it sounds like a home directory thing...
A nooby friend of mine had a similar problem when he tried mounting his windows partition to his home directory. This is probably not your problem, but something is stopping your home directory from working/mounting. Blowing away a Linux partition to reinstall wont take long, even on my PXE booted 600MHz laptop it will only take an hour to install, and another hour of configuring.

---

### Post by fordfan753 on 2005-09-22
[QUOTE=mathias]
I shut down my computer and restarted trying to boot into Ubuntu.
It started to boot and then stopped saying something that there was an Superblock Error and it couldn't mount /dev/hda7.
/Mathias[/QUOTE]

Did you edit your /etc/fstab to reflect your file system changes?
It should now say vfat instead of ntfs in the file system type column for the file system you changed. Is that partition /dev/hda7 ?

---

### Post by mathias on 2005-09-22
No, I haven't made any changes since making the convertion, but I'm not sure if Ubuntu has mounted that drive anyway...

Does the Ubuntu installation mount the other drives automatically? (I didn't check if they we're mounted after installation...

How do I edit the /etc/fstab???

---

### Post by mathias on 2005-09-22
Ok, so this is the exact error message I recieved:

============================================

Fsck.ext3: Bad Magic number in super-block while trying to open /dev/hda7.
/Dev/hda7: The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and not swap or UFS or something else), then the superblock is corrupt, and you might try running E2fsck with an alternate superblock:
E2fsck -b 8193 <device>

*   [Fail]

Fsck failes. Please repair manually.

Control-D will exit from this shell and continue system startup.

==============================================

So, the /Dev/Hda7 is my swap (I checked when I re-partitioned the disc and re-installed Ubuntu), so the superblock shouldn't be corrupt, but still, why doens't Ubuntu startup and use the swad-drive as intended?

Anyone who can help me? How can I do this manually?

---

### Post by fordfan753 on 2005-09-23
[QUOTE=mathias]Ok, so this is the exact error message I recieved:

============================================

Fsck.ext3: Bad Magic number in super-block while trying to open /dev/hda7.
/Dev/hda7: The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and not swap or UFS or something else), then the superblock is corrupt, and you might try running E2fsck with an alternate superblock:
E2fsck -b 8193 <device>

*   [Fail]

Fsck failes. Please repair manually.

Control-D will exit from this shell and continue system startup.

==============================================

So, the /Dev/Hda7 is my swap (I checked when I re-partitioned the disc and re-installed Ubuntu), so the superblock shouldn't be corrupt, but still, why doens't Ubuntu startup and use the swad-drive as intended?

Anyone who can help me? How can I do this manually?[/QUOTE]

Hmm, if that really is your swap then why it fsck saying that there is no valid ext2 filesystem. Swap does not use ext2! If /dev/hda7 is swap then typing:
```
cat /etc/fstab
```
should return something with a line like
```
/dev/hda7       none            swap    sw              0       0
```
If not, then you may have to change you fstab. Do this with:
```
sudo gedit /etc/fstab
```
Maybe if you post the results of:
```
cat /etc/fstab
```
it will be easier to see what your partitions are like. Also post the output from:
```
sudo fdisk -l /dev/hda
```

---

