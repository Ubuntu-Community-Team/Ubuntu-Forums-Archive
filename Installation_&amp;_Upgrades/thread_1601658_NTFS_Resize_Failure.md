---
title: "NTFS Resize Failure"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by joshuarowley42 on 2010-10-20
Hi All,

I am just logging down a couple of experiences that I have had earlier today, in the hope that it may be of use to someone else!

I wanted to resize an NTFS partition on a friends computer to make space for Ubuntu. I followed the guide on [this]("http://crashrecovery.org/CrashRecoveryKit/iso/2.6.11.10/HOWTO.ntfs.html") website to the letter, tried to remount the resized partition and it failed with the standard error:

```
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```

Now, the first thing I did was to panic. I remembered Douglas Adams' advice and continued as follows; 

After plenty of searching, it dawned on me that in deleting and creating a partition, I may have started the partition at the correct cylinder, but NOT NECESSARILY THE CORRECT SECTOR. 

If you have not made this mistake yet, but are doing your research - make sure you use the "-u" option:
```
# fdisk -u /dev/sda
```
and when recreating the new partition, make sure you create it at the correct starting sector. 

For those of you who have already made this mistake and are now looking for a solution; here is what I did, it was not pretty. I will leave out all my thought processes and just explain what I found to work. 

What you need to do is find the start of the NTFS file-system and configure the partition to start there. 

The following command effectively searches the disk for raw ASCII, looking for a string, in this case BOOT, I tried other terms, like NTFS, NT and anything else I could think of that was likely to be in the boot-loader. This you will need to tweak, to find what works for you. 

```
# dd if=/dev/sda skip=0 count=1000 bs=512 | hexdump -C | grep BOOT
```
(note, if your I/O size is different, 512 may not be appropriate)

If nothing is returned (except dd telling you how many bytes have been in and out), then try removing the grep part of the command to check if you have indeed found anything other than zeros.
If only zeros have been found, the result is likely to look something like this:
```

rowley@lx42:~$ sudo dd if=/dev/sda1 skip=0 bs=512 count=1 | hexdump -C 
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000200
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.00036848 s, 1.4 MB/s

```

Keep increasing "count=x" until you find something that looks meaningful - what exactly this is, or will look like; I am sorry, I just don't know :(. But for me it was some boot-loader code, recognizable from the days when I used to run windows - "Push Ctl+Alt+del" or something like that. 

On the left hand side of the hex output, there is a line number - e.g. "000013b0", to convert this into a position that you can give to dd, simply divide by 512. 
```

rowley@lx42:~$ python 
>>> 0x0007c000/512
992

```

Once you figure out how many bytes into the disk the partition starts, (which in my case was at 2048), it is possible to recreate your partition in the right place. 

If you were using a bs=512 with dd, and your Sector size is also 512 bytes (run fdisk -l /dev/sda to find out), then your start sector will also be 2048. (since 2048*512/512=2048). 

So to complete, open up fdisk (using fdisk -u this time), delete the existing partition that you created, and recreate it, with the appropriate start sector. Given that you resized, you will need to set the correct end-position as well (or at least leave enough space). If like me you were too terrified to mess any more, just leave the end-position at the end of the disk, back everything up, and start again!


I hope this has been of some help to someone, if people find this useful, or need any more information on what I did, reply and I will include it in the post. If it seems that it is useful to more than a select few, I may even write a little clearer English!


LX

---

