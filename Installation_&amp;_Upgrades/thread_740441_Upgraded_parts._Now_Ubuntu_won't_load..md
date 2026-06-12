---
title: "Upgraded parts. Now Ubuntu won't load."
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by DocHolliday2006 on 2008-03-30
Hi. I just replaced my power supply, cpu, motherboard, and video card because my mobo was having issues and I took the opportunity to upgrade. I need the info on my hard drive, so I can't reformat it or anything.

The motherboard and CPU are the same socket/ chipset (Nvidia/ 939) as before. The ram is the same from my old build and it is compatible. The graphics card is just 1 step up from the old nvidia card. 

So I put my computer back together and hit power and the Ubutnu loading bar goes by very slowly. 

Then it gets to a black screen and basically tells me why it can't load. There are a ton of things listed, but here are some:

Bus Error
173.00550 Buffer I/O error on device sdal, logical block 10977296
----------
chmod: cannot access/var/log/dmes.new - no such file or directory
-----------
Touch: error while loading shared libraries /Lib/Librt.so.1


Anyone know what is going on and how I can fix it?

Thanks for your time,
-Andrew

---

### Post by dstew on 2008-03-30
Can you boot in recovery mode?

---

### Post by DocHolliday2006 on 2008-03-30
So I just booted into recovery mode and it gave me an error message: "Inconsistent File Structure." I then hit enter and it brought me back to the menu.

---

### Post by DocHolliday2006 on 2008-03-30
So I tried booting in with my live cd.

I got onto the desktop and went to Terminal

So I type:

Sudo grub

I get to the grub menu

But when I try to type: 
root (hd0,1) it said it can't find it
I was going to type setup.

I think that would do it.

Could someone give me straight forward instructions on what I need to do to get my Hard drive to boot?

BTW, when I go to 

"Place"
"Computer"

and click on my hard drive, my computer crashes out of the live cd and reboots.

Don't know if that is relevant.

Thanks.

---

### Post by NullHead on 2008-03-30
Boot to your live CD and type this in to repair your filesystem: ```
sudo fsck.ext3 -f /dev/<devicename>
```
<devicname> will probably be sda1, sdb1, hda1 or hdb1. Try all of those device names unless you know it already. This should fix it all up.

---

### Post by DocHolliday2006 on 2008-03-31
"sudo fsck.ext3 -f /dev/<devicename>"

I type this into the console in the live CD boot and it says "The superblock could not be read or does not describe a correct ext2 filesystem."

BTW, as far as I know, my install directory is default. 

What does this mean?

---

### Post by PmDematagoda on 2008-03-31
Can you post the output of:-
```
sudo fdisk -l
```
in the Live CD.

---

### Post by DocHolliday2006 on 2008-03-31
When I type that in it reads:

Disk/dev/sda : 320.0 GB

/dev/sda1 -Linux
/dev/sda2 - Extended
/Dev/Sda5- Linux Swap / Solaris


> **PmDematagoda said:**
> Can you post the output of:-
```
sudo fdisk -l
```
in the Live CD.

---

### Post by DocHolliday2006 on 2008-03-31
OK. I did what is below and could not proceed. What do I do from here?

ubuntu@ubuntu:~$ sudo fsck.ext3 -f/dev/hda1
fsck.ext3: invalid option -- /
Usage: fsck.ext3 [-panyrcdfvstDFSV] [-b superblock] [-B blocksize]
                [-I inode_buffer_blocks] [-P process_inode_size]
                [-l|-L bad_blocks_file] [-C fd] [-j external_journal]
                [-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
ubuntu@ubuntu:~$ -P process_inode_size
bash: -P: command not found
ubuntu@ubuntu:~$ -p
bash: -p: command not found
ubuntu@ubuntu:~$

---

### Post by NullHead on 2008-03-31
That should be: ```
sudo fsck.ext3 -f /dev/hda1
```

---

### Post by kaginken on 2008-04-01
Let me see if I got this right.  You just replaced your power supply, cpu, motherboard, and video card, now you're trying to get ubuntu to boot up?  :lolflag:

Think it's time to reinstall your OS?

---

### Post by NullHead on 2008-04-01
> **kaginken said:**
> Let me see if I got this right.  You just replaced your power supply, cpu, motherboard, and video card, now you're trying to get ubuntu to boot up?  :lolflag:

Think it's time to reinstall your OS?

NO .. all that's wrong is a broken filesystem. fsck.ext3 can fix this no problem.

---

### Post by DocHolliday2006 on 2008-04-01
So I did that. IT said something about retrieving a journal file or something.Then my computer restarted. I took out the CD and it tried to load from my hard drive. It said: Error16: inconsistent file system structure. 

What does this mean and what should I do?


> **NullHead said:**
> That should be: ```
sudo fsck.ext3 -f /dev/hda1
```

---

### Post by NullHead on 2008-04-01
Did you happen to write down what it said before it restarted? Did it complain about it being mounted? You can check if the hard drive is mounted by: ```
df
```That will report all mounted devices. Look for /dev/hda1 if you don't see it in the list, than it isn't mounted. 

Lets try this another way. Use this instead next time you boot into the livecd. ```
sudo fsck.ext3 -p /dev/hda1
```
Please notice the space after the -p

---

### Post by DocHolliday2006 on 2008-04-01
Ok. Tried Code df and got this:

ubuntu@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                  1037452     15444   1022008   2% /lib/modules/2.6.22-14-generic/volatile
tmpfs                  1037452     15444   1022008   2% /lib/modules/2.6.22-14-generic/volatile
varrun                 1037452        88   1037364   1% /var/run
varlock                1037452         0   1037452   0% /var/lock
udev                   1037452        60   1037392   1% /dev
devshm                 1037452         0   1037452   0% /dev/shm
tmpfs                  1037452        12   1037440   1% /tmp
ubuntu@ubuntu:~$ 

Tried second bit of code and got this:

ubuntu@ubuntu:~$ sudo fsck.ext3 -p /dev/hda1
fsck.ext3: No such file or directory while trying to open /dev/hda1
/dev/hda1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

What should I do now?


[QUOTE= You can check if the hard drive is mounted by: ```
df
```That will report all mounted devices. Look for /dev/hda1 if you don't see it in the list, than it isn't mounted. 

Lets try this another way. Use this instead next time you boot into the livecd. ```
sudo fsck.ext3 -p /dev/hda1
```
Please notice the space after the -p[/QUOTE]

---

### Post by wannadumpwindows on 2008-04-01
Back on the first page, the command returned that the file system was on /dev/sda, shouldn't he be using that at the command line, rather than /dev/hda??

---

### Post by DocHolliday2006 on 2008-04-01
I tired that:

ubuntu@ubuntu:~$ sudo fsck.ext3 -p /dev/sda
fsck.ext3: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$ 



> **wannadumpwindows said:**
> Back on the first page, the command returned that the file system was on /dev/sda, shouldn't he be using that at the command line, rather than /dev/hda??

---

### Post by NullHead on 2008-04-01
> **wannadumpwindows said:**
> Back on the first page, the command returned that the file system was on /dev/sda, shouldn't he be using that at the command line, rather than /dev/hda??

I think I didn't read it all correctly if what you seen was /dev/sda than lest try this with sda. ```
sudo fsck.ext3 -f /dev/sda1
```

---

### Post by DocHolliday2006 on 2008-04-02
It did this:

ubuntu@ubuntu:~$ sudo fsck.ext3 -f /dev/sda1
e2fsck 1.40.2 (12-Jul-2007)

Pass 1: Checking inodes, blocks, and sizes


Then the computer restarted after another minute. Not sure if there were supposed to be other passes.

What does that mean?

> **NullHead said:**
> I think I didn't read it all correctly if what you seen was /dev/sda than lest try this with sda. ```
sudo fsck.ext3 -f /dev/sda1
```

---

### Post by NullHead on 2008-04-02
> **DocHolliday2006 said:**
> It did this:

ubuntu@ubuntu:~$ sudo fsck.ext3 -f /dev/sda1
e2fsck 1.40.2 (12-Jul-2007)

Pass 1: Checking inodes, blocks, and sizes


Then the computer restarted after another minute. Not sure if there were supposed to be other passes.

What does that mean?

It restarted instantly as if the button were pushed??!! If this is the case I would dare to guess that your hard drive had died as well :( ... but if it finished and *then* YOU restarted it, than everything is fine. 

What the command does, the one I gave to you earlier, forces a filesystem check on your hard drive, /dev/**sda1**, and it's supposed to optimize the folders, check for errors and fix any errors that are there.

---

### Post by wannadumpwindows on 2008-04-02
Yeah, I shoulda been more specific, sorry about that.

---

### Post by louieb on 2008-04-03
Just wondering what BIOS says about your hard drive. 
May be something simple. If its an IDE drive try setting detection to AUTO and mode to LBA or AUTO.

---

### Post by pooyaplus on 2008-07-05
> **louieb said:**
> Just wondering what BIOS says about your hard drive. 
May be something simple. If its an IDE drive try setting detection to AUTO and mode to LBA or AUTO.

I have a similar problem and tried all the grub error 18 advices with no success. What I got from the googling and the forum suggestion is that the hard drive might be defective.:(

---

