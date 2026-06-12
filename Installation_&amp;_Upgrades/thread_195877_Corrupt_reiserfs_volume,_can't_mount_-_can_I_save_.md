---
title: "Corrupt reiserfs volume, can't mount - can I save the data?"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by sog on 2006-06-13
not sure this is the right forum for this question, but couldn't find something more appropriate. basically, after a hard reset of my Thinkpad, i ended up w/ (maybe) a damaged hard drive and (definitely) some corruptions of the reiser root partition. a Windows XP on the partition, incidentally, boots just fine. 

after running a reiserfsck --rebuild-tree /dev/hda4 i got the following:


"bread: Cannot read the block (5549459): (Input/Output error).

The problem has occured looks like a hardware problem. If you have bad blocks, we advise you to get a new hard drive, because once you get one bad block that the disk drive internals cannot hide from your sight, the chances of getting more are generally said to become much higher...

If you don't want to follow that follow that advice then if you have just a few bad blocks, try writing to the bad blocks and see if the drive remaps the bad blocks 9that means it takes a block that it has in reserve and allocates it for use for of that bluck number). If it cannot remap the block, use badblock option (-B) with reiserfs utils to handle this block correctly."

at this point, i can neither boot into the volume (kernel panic) or chroot into it (won't mount volume). 

i'm still hoping, however, that there's some way i can at least get in and extract some of the data i have not yet backed up. 

anybody have any ideas?

---

### Post by jaa1180 on 2006-06-13
You could try booting with a live CD, Gentoo always works good, and see about doing a 'dd' of the HDD to another location. 

Do you have another HDD to move the files to?

---

### Post by sog on 2006-06-13
hi jaa1180 - really appreciate the response. 

i've got the LiveCD available, so that part's easy, but i'm unclear on what's being proposed. are you saying dump the actual contents of the disk to another hard drive? 

does dd allow me to do that without even being able to mount the drive in question? and wouldn't i simply replicate the bad reiser tree on the second drive? 

definitely willing to try this if you think it'll work, and i have some extra hard drive space on other machines on my network.

---

### Post by jaa1180 on 2006-06-13
[QUOTE=sog]hi jaa1180 - really appreciate the response. 

i've got the LiveCD available, so that part's easy, but i'm unclear on what's being proposed. are you saying dump the actual contents of the disk to another hard drive? 

does dd allow me to do that without even being able to mount the drive in question? and wouldn't i simply replicate the bad reiser tree on the second drive? 

definitely willing to try this if you think it'll work, and i have some extra hard drive space on other machines on my network.[/QUOTE]

No, you don't need to mount with the DD command.
```
dd if=/dev/whateverthedeviceis of=/path/to/dump
```

You can even dump it to an ISO file and then mount the file. 
```
dd if=/dev/whateverthedeviceis of=/path/to/dump/nameit.iso
```

On the "of" part, just name the file and put ".iso" on the end. 
Do a google search for "linux dd command"

You can do it! :p

---

### Post by sog on 2006-06-13
excellent news - thx for following up jaa1180. 

will definitely dump the partition in question - i just need to be able to mount another drive on the network to do that. that i can figure out. 

my question to you is: once i've successfully dumped the volume - whether it's straight up or in ISO form, what's the next step? what do i do with that file? how do i extract the information i need from it?

---

### Post by jaa1180 on 2006-06-13
[QUOTE=sog]excellent news - thx for following up jaa1180. 

will definitely dump the partition in question - i just need to be able to mount another drive on the network to do that. that i can figure out. 

my question to you is: once i've successfully dumped the volume - whether it's straight up or in ISO form, what's the next step? what do i do with that file? how do i extract the information i need from it?[/QUOTE]

Ok, here is the easy part. 
If you did a straight dump, it is just another file system. So if you dumped it to another disk, you just mount that disk. 

Personally, I would do the ISO file. After it is done, mount the iso file. CD to that directory you mounted it and Volia, you now are seeing the files. 

What is the dev name? Where is it going to? I will give a step by step... you can fill in the rest...

---

### Post by sog on 2006-06-14
thanks so much for all the help. i successfully mounted an external usb 2.0 hdd and did a dd if=/dev/hda4 of=/mnt/external/hda.iso, but i'm getting 'file size limit exceeded error'. is there any way around that?

update: just cd'd to the target dir and did a ulimit -a, and the file size says 'unlimited'

---

### Post by jaa1180 on 2006-06-14
Someone can correct me if I am wrong... but I think you don't give it a partion but the whole device.
```
dd if=/dev/hda of=/mnt/external/hda.iso
```

If I am thinking right, you are coping bit by bit... so it is the whole device.
I could be wrong though. The above is the way I have done it in the past.

---

### Post by jaa1180 on 2006-06-14
[QUOTE=jaa1180]Someone can correct me if I am wrong... but I think you don't give it a partion but the whole device.
```
dd if=/dev/hda of=/mnt/external/hda.iso
```

If I am thinking right, you are coping bit by bit... so it is the whole device.
I could be wrong though. The above is the way I have done it in the past.[/QUOTE]

Of course make sure you external HDD is larger than what you hda is... just in case. I know it is trivial but I have done it.... :)

---

### Post by sog on 2006-06-14
ok, makes sense. will go ahead and try that now. fortunately, the external drive is much larger than the device, so we're good on that score. 

will let know how it turns out.

---

### Post by sog on 2006-06-14
tried that, got the same error - file size limit exceeded. :(

---

### Post by sog on 2006-06-16
tried to dump to a different external drive; same results. anybody got an ideas?

---

### Post by audax321 on 2006-06-17
Do you know what filesystem the external hard drive uses? Just a thought but the file size exceeded warning might not mean that the capacity of the device has been exceeded but that the filesystem on the external hard drive just can't support a file that large.  

For example, FAT16 has a 2GB file size limit and FAT32 (a popular format for external drives) has a 4GB file size limit. If the iso file is exceeding these bounds, that might be causing the error.

---

### Post by sog on 2006-06-18
it's FAT32, and i've been advised that that has a 4 GB limit on file size - regardless of what ulimit may tell me. 

so my next step is trying to determine if/how to dd out to another drive on a networked machine rather than something local, as i don't have a spare external drive that's ext3 formatted.

---

### Post by audax321 on 2006-06-20
Here are two methods I found. Netcat, should already be installed in Ubuntu.

See tutorials here: [http://gentoo-wiki.com/HOWTO_Backup#Backing_up_a_whole_partition_on_a_remote_machine](http://gentoo-wiki.com/HOWTO_Backup#Backing_up_a_whole_partition_on_a_remote_machine)

The first method ('Backing up a whole partition on a remote machine') will dd the contents of the Reiser partition you are trying to backup, gzip it, and send it to the remote computer.

You should be able to create an iso by getting rid of the gzip command and changing the name of the output file on the remote computer from image.gz to image.iso  But, I'm honestly not sure if that will work. Otherwise it will make a gzipped image of the Reiser filesystem that is already on that hard drive... which may or may not work since the original computer can't even mount it.

The second method ('Securely backing up a filesystem on a remote machine') is using a subdirectory as the backup source... since you can't mount it may not work. If you're network is secure and no one is hacking you or anything the first method would probably be quicker and easier.

I've never had to do a backup like this before, but let me know how it works out. Good luck.

---

### Post by arjay1 on 2006-06-20
Following this thread closely as i have a similar disaster.  If anyone is still around in this thread - my problem is that the corrupted drive is 200Gb (reiserFS formatted) and I don't have anything like that available to dd to.  The best I have is 20-30GB available on another HD.

Is it possible just to dd part of a drive or otherwise just view the contents?


Thanks - it is panic and despondency this end so any help really appreciated.:oops: 

RJ

---

### Post by jaa1180 on 2006-06-20
You may want to see if you can copy off data with a live CD. I recommend Gentoo live CD, or Knoppix. The best. Sorry, Ubuntu does not hold a candle against those two.

---

### Post by arjay1 on 2006-06-20
jaa1180

Thanks for contributing.  I am currently trying to copy the data via the dd command (got from another post).  However, it makes an .iso image of the disk as it exports it.  Unfortunately, the corrupted disk is 200GB and unfortunately, the only other disks I have a re 40 GB - thus the iso will be too big, so I am stumped at the moment.  I'll download the knoppix live CD if you think it is worth it.  Do you know what the software is that they have?
RJ

---

