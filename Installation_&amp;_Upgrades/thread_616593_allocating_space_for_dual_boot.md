---
title: "allocating space for dual boot"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by delilahjed44 on 2007-11-18
Hello, I have been on line researching what exactly I should do here, I will go through Live Cd with Ubuntu 7.10 to partition the disk, if this does not work I hope to get back to Ubuntu and try the G-parted.

History on my pc as of space Windows XP and Linux Live:

Windows Xp C-drive...9.93 GB used 26.GB free.
total physical > 768 MB 
Available > 455.49 MB

Here is what I see in 7,10:
/dev/sda1/ NTFS 39251 MB
/dev/sda5 swap 764 MB

Used in 7.10:
NTFS 10700 MB
Swap 764 0 MB

I am not sure exactly what to propose in the box marked 764 in Linux for a swap...

I just need the the skinny with experience to say, yes this is ok before i move on..

My choice is to allocate the space in question to  264 MB, this would be for the new partition for Linux, giving me 3rds back in Windows for programs as yet being used.  Ok, does this sound about right, I though if I ran into any up-heavals and sorry...I am sure I will, but I resort to this if Linux becomes more inquisitive to an exact.

264 megabytes (informal notation: kilobyte = 1024 bytes) 
bits 2214592512 
bytes 276824064 
kilobits 2162688 
kilobytes 270336 
megabits 2112 
megabytes 264 
gigabits 2.0625 
gigabytes 0.2578125 
terabytes 0.00025177001953125 
petabytes 2.45869159698486e-07 
Source code  

Hopefully not, but I have never accomplished a dual boot as yet.  

Thank you.. all of you...I know I am a pain...

Be happy I am not a twin :)

---

### Post by zvacet on 2007-11-18
It is seams that you have only one partition.Defragment it few times before you shink it.You can shrink it with 

[http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")

and leave unallocated space.On that space you will install Ubuntu.

---

