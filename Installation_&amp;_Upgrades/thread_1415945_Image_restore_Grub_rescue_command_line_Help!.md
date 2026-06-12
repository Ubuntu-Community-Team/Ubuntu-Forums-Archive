---
title: "Image restore Grub rescue command line Help!"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by frisbeeguitar on 2010-02-25
Please Help!
 
I do computer forensics here in Afghanistan and I am trying to keep a clean image of a dual bootable hard drive. Here is what I try to do...
 
1. Boot into UbuntuLiveCD
2. I run "sudo dd if=/dev/zero of=/dev/sda conv=sync,notrunc bs=64K" to wipe the drive with all zeros.
3. I then install Windows by creating a new partician about 50GB.
4. I then install Linux by creating a partician in ext4 mounting it at '/' in addition I create a swap partician.
5. Next configure everything just the way I want it. I install all the drivers and software I need for my windows partician and build out the remaining part of the disc as a "data drive."
6. Then I use "dd" again to try to image my "clean slate" of a system. Remember I am dual booting. I dd the /dev/sda and gzip it.
7. When I go to restore it, I boot from the live CD again and unzip ig and "dd" it back onto /dev/sda.
8. I run fdisk -l and I get:
/dev/sda1 * 1 6375 5120000000 7 HPFS/NTFS
/dev/sda2 6376 11724 42965842+ 83 Linux
/dev/sda3 11725 12453 ...... 82 Linux swap / Solaris
This means to me that it can "understand the file system"
9. But then when I take out the Live boot CD and try to get my "clean slate" machine back, the system goes into Grub Rescue mode with a grub command line "grub rescue>"
10. I tried using the tutorial on Grub2, but...
a. It would not understand the command "linux" 
b. When I try to do insmod, it says it doesn't recognize the file system.
 
Please help!
 
Here is one tidbit of information that may be of some value... when I restore the image and then still in the Liveboot, when I try to mount either the NTFS or the Linux particians, I get errors. 
 
The error I get when trying to mount the linux (Ubuntu 9.10) partician is:
sudo mount -t ext4 /dev/sda2 /media/drive
mount: wrong fs type, bad option, bad superblock on /dev/sda2, 
missing codepage or helper program or other error
In some cases useful info is found in syslog -try
dmesg | tail or so
 
 
Thank you!

---

### Post by ImTheBatman on 2010-02-25
the word "partition" is spelled with "tion", not with "cian"

---

### Post by Scottydoesntknow on 2010-02-27
> **ImTheBatman said:**
> the word "partition" is spelled with "tion",  not with "cian"

Your post contributes absolutely nothing to solving the OP's problem.  
Congratulations on perpetuating the Linux snob stigma.

---

### Post by louieb on 2010-02-27
Sounds like you did things right. Something got screwed up. Take a look.

Get the [Boot Info Script: SourceForge.net:]("http://bootinfoscript.sourceforge.net/")  and
put your results.txt in your next post

---

### Post by frisbeeguitar on 2010-03-01
All,
 
I was able to fix it. What appears to be the problem was that when I was using the "dd" command, I used a block size of 64K per reccomendations from some website. 
 
[http://www.linuxweblog.com/blogs/sandip/20050211/image-your-hard-drive-using-dd](http://www.linuxweblog.com/blogs/sandip/20050211/image-your-hard-drive-using-dd)
 
Instead I used a bock size of 512 and it appears to have worked! System restored!
 
Louieb, before I did that I tried the script and it was very helpful! Thanks for your help!
 
ImThBatman, thank you for correcting my spelling.
 
ScottyDoesn'tKnow, thanks for sticking it to the Bat! :) But I am guessing you are unwilling to try linux? You should try it! I'll bet you are really good at Windows and computers overall, just a little timid to step into new waters...
 
:KS
 
P.S. Ubuntu Forums rocks!

---

