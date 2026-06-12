---
title: "I dunno what to call it..."
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by tracetheace on 2008-09-07
Alright, I boot off the Ubuntu CD and select the 'install unbuntu' option. A dialogue pops up and shows a progress bar of the kernel being loaded. Then the Ubuntu loading screen comes up, during that the screen goes black and then I'm stuck in some sort of terminal called busybox. 

Now by removing the quietsplash at the end of the line I can see that there's an error repeating over and over.
```
hda: status error: status = 0x59 {DriveReady SeekComplete DataRequest error}
hda: status failed error: error = 0x00 {}
ide: falied opcode was: unknown
hda: drive not ready for command
```

This also happened when I tried to install LinuxMint.
Now I did install ubuntu, but through the cd while I was booted into windows. I would like to do a full install that uses the entire disk.

I obviously don't know what it causing this problem, cause I'm just a noob. But my first guess is perhaps a bug in the linux kernel... I find that unlikely.

Any help would be greatly appreciated.
Thanks.

---

### Post by Sef on 2008-09-07
More likely a problem with your hard drive.  **Back up **your data first, if you have not already.  Check your hard drive with fsck:  [man pages]("http://www.manpagez.com/man/8/fsck/") and [tutorial]("http://adminschoice.com/docs/fsck.htm").

---

### Post by tracetheace on 2008-09-07
I doubt it's my hard drive.
I tried again but this time I added 'all_generic_ide' at the end of the line. Which actually worked, went through the entire install process without any problems.

Once it came time to actually boot of the hard drive with ubuntu now installed on it. Grub comes up and give me an error.
I didn't write it down, but it says something like Error 15 something.

I'll try again and write down the error and post back.

---

### Post by tracetheace on 2008-09-07
Alright, so I tried installing Linux Mint to see if the same problem would occur. It did.
```
Booting 'Linux Mint, Kernel 2.6.24-16-generic'
Filesystem type is ntfs, partition type 0x7
Kernel /boot/vmlinuz-2.6.24-16-generic root=/dev/sda1 ro quiet splash
Error 15 : File not found
```

I know '/dev/sda1' is the drive I installed linux onto, my other drive is for windows.

Anyone know anything about this?
Thanks.

---

### Post by caljohnsmith on 2008-09-07
> **tracetheace said:**
> Alright, so I tried installing Linux Mint to see if the same problem would occur. It did.
```
Booting 'Linux Mint, Kernel 2.6.24-16-generic'
[COLOR="Red"]Filesystem type is ntfs, partition type 0x7[/COLOR]
Kernel /boot/vmlinuz-2.6.24-16-generic root=/dev/sda1 ro quiet splash
Error 15 : File not found
```

I know '/dev/sda1' is the drive I installed linux onto, my other drive is for windows.

Anyone know anything about this?
Thanks.
Well for one thing, you need to use a file system like ext2 or ext3 for your linux distros, and not NTFS which is Windows. :)

---

### Post by tracetheace on 2008-09-07
Alright so I followed this guys guide on how to partition my drive.
Just so you know I have a seperate HDD that I'm trying to install onto. Not trying to create a partition on my windows drive and complicate things.

[http://www.dedoimedo.com/computers/install_linuxmint_2.html](http://www.dedoimedo.com/computers/install_linuxmint_2.html)
I figure the partition setup is the same in mint as in ubuntu.
Even with following this chaps directions, I still get the same error...
Not only did I try the manual way, I also used to used the automatic partition creator.

I'm really starting to get frustrated, I know this probably isn't a regular problem. But honestly I'm starting to think about giving up here.

---

### Post by tracetheace on 2008-09-08
Okay sooo apparently GRUB wasn't automaticly configured properly to chose the right drive. It was trying to access (hd0,1) instead of the proper (hd1,1) where linux is installed.

I have to wonder, how does a NUB like me figure this out on his own pretty much...

Thanks for the help. :roll:

---

### Post by father time on 2008-09-08
Message Deleted.

---

