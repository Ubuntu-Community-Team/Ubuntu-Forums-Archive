---
title: "error when resize/move ext3 paryition + cannot save error details"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by rudedcam on 2009-12-13
[[IMG]http://imgur.com/ZnFIOs.png[/IMG]](http://imgur.com/ZnFIO.jpg)

I have encountered an error preventing GParted from completing the Move/Resize operations that I would like to see append (always around 45-50%). The error occurs when gparted "move to the right and shrik" my ext3 (ubuntu) partition. the goal is to give up ext3 space in front of my ntfs (vista is to be grown) partition

The error message says that for help I should follow the directions on this site:

[http://gparted.sourceforge.net/larry/tips/save_details.htm](http://gparted.sourceforge.net/larry/tips/save_details.htm)

Unfortunately, I have had no luck saving the details to USB stick.

So my problem, basically, is two problems:  1.) I can't get gparted to work for me, and 2.) I can't save the details of gparted's attempt at partitioning (making changes to) the drive.

I used "Parted magic" (latest version), GParted live cd (newest stable version and 0.3.6-7). same problem every single time.
I have a dell inspiron

tanks for any help on the matter 
cam

---

### Post by darkod on 2009-12-13
Did you try to boot with ubuntu/kubuntu cd, select Try Ubuntu option and then use Gparted? On this screenshot /dev/sda5 is mounted, how do you expect to move it? And if you boot your hdd install you can't unmount root.
You need to boot with the cd, then root is not mounted and if swap is use right click swapoff.

---

### Post by rudedcam on 2009-12-13
> **darkod said:**
> Did you try to boot with ubuntu/kubuntu cd, select Try Ubuntu option and then use Gparted? On this screenshot /dev/sda5 is mounted, how do you expect to move it? And if you boot your hdd install you can't unmount root.
You need to boot with the cd, then root is not mounted and if swap is use right click swapoff.

What i have initially done was to boot from the gparted live cd. same problem.
i've then booted on RAM with patedmagic (screenshot you've seen).
i didn't use at any time the ubuntu cd.

upon reading your suggestions, i've booted partedmagic "live with default settings". however, sda5 hasn't been mounted nor did the linux-swap. (unmount isn't an option or is greyed out)
from what i understand, when something is mounted, there's a padlock icon on the partition line, which isn't the case here.

since i've booted with a live cd (partedmagic) root hasn't been mounted. and nothing else was mounted either. still no success.
Am i getting this right?

maybe i didn't understand your post, tell me so if that's the case. otherwise do you have any ideas from there?

cam :D

---

### Post by darkod on 2009-12-13
I haven't used partedmagic and only once Gparted LiveCD. So I can't comment on them.
Yes, usually there is padlock if it's mounted, but then why in the Mount Point column there are values? /media/etc
Why not empty like with the swap partition?
Why don't you give the ubuntu/kubuntu cd a go? I don't know what else to suggest. You seem to be doing it right.

---

### Post by rudedcam on 2009-12-13
quick question, once booted from ubuntu live cd, what program do you use?
partition editor?
qtparted?

or anything else for that matter?

---

### Post by darkod on 2009-12-13
Gparted, in System-Administration.

---

### Post by rudedcam on 2009-12-13
yup, i have tried with partition editor (GParted) and i still get the same error.
there must be a solution. somehow!

---

### Post by rudedcam on 2009-12-13
> GParted 0.4.3

Libparted 1.8.8
Move /dev/sda5 to the right and shrink it from 161.66 GiB to 161.66 GiB  00:31:36    ( ERROR )
     	
calibrate /dev/sda5  00:00:01    ( SUCCESS )
     	
path: /dev/sda5
start: 92245293
end: 431281052
size: 339035760 (161.66 GiB)
calculate new size and position of /dev/sda5  00:00:00    ( SUCCESS )
     	
requested start: 133211043
requested end: 472246739
requested size: 339035697 (161.66 GiB)
new start: 133210980
new end: 472246739
new size: 339035760 (161.66 GiB)
check file system on /dev/sda5 for errors and (if possible) fix them  00:04:57    ( SUCCESS )
     	
e2fsck -f -y -v /dev/sda5
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

195296 inodes used (1.84%)
3359 non-contiguous files (1.7%)
195 non-contiguous directories (0.1%)
# of inodes with ind/dind/tind blocks: 14329/943/1
15270463 blocks used (36.03%)
0 bad blocks
4 large files

151148 regular files
24621 directories
69 character device files
26 block device files
2 fifos
405 links
19409 symbolic links (17736 fast symbolic links)
12 sockets
--------
195692 files
e2fsck 1.41.4 (27-Jan-2009)
move file system to the right  00:26:38    ( ERROR )
     	
perform read-only test  00:26:38    ( ERROR )
     	
using internal algorithm
read 339035760 sectors
finding optimal blocksize
     	
read 65536 sectors using a blocksize of 128 sectors  00:00:03    ( SUCCESS )
     	
65536 of 65536 read
3.19658 seconds
read 65536 sectors using a blocksize of 256 sectors  00:00:03    ( SUCCESS )
     	
65536 of 65536 read
2.40429 seconds
read 65536 sectors using a blocksize of 512 sectors  00:00:02    ( SUCCESS )
     	
65536 of 65536 read
2.1704 seconds
read 65536 sectors using a blocksize of 1024 sectors  00:00:02    ( SUCCESS )
     	
65536 of 65536 read
2.21266 seconds
read 65536 sectors using a blocksize of 2048 sectors  00:00:02    ( SUCCESS )
     	
65536 of 65536 read
1.4977 seconds
read 65536 sectors using a blocksize of 4096 sectors  00:00:01    ( SUCCESS )
     	
65536 of 65536 read
1.73827 seconds
read 65536 sectors using a blocksize of 8192 sectors  00:00:01    ( SUCCESS )
     	
65536 of 65536 read
0.974395 seconds
read 65536 sectors using a blocksize of 16384 sectors  00:00:02    ( SUCCESS )
     	
65536 of 65536 read
1.54502 seconds
read 65536 sectors using a blocksize of 32768 sectors  00:00:01    ( SUCCESS )
     	
65536 of 65536 read
1.12358 seconds
read 65536 sectors using a blocksize of 65536 sectors  00:00:01    ( SUCCESS )
     	
65536 of 65536 read
1.15833 seconds
optimal blocksize is 8192 sectors (4.00 MiB)
read 338380400 sectors using a blocksize of 8192 sectors  00:26:20    ( ERROR )
     	
142419568 of 338380400 read
Error while reading block at sector 288197933
143074928 sectors read
libparted messages    ( INFO )
     	
Input/output error during read on /dev/sda.

---

