---
title: "Installing ubuntu with windows installed as well"
date: 2011-06-08
forum: Installation &amp; Upgrades
---

### Post by kainu7 on 2011-06-08
Hey guys totally new to this, ill give you what ive done so far.
its 500gig hd and 4gig of ram.

So i backed up all my stuff from windows 7, reformated partitioned 100gig off for windows, leaving 368gig unallocated. 

so i have windows 7 installed now, i put ubuntu 11.04 in, click install, english, click "something else" since i have that 368gig of unallocated space.  

Click freespace add..

now im lost, 
it asks 
Type for the new partition: Primary or Logical (i dont know)
New partition size: I get this one.
Location for the new partition: beginning or end (i dont know)
use as: ext4,ext3, JFS, XFS, FAT16, FAT32, ect.ect.ect. (i dont know)
Mount Point: / /boot /home /tmp ect,ect,ect ( i dont know)


so what do i do at this point? if anyone can tell me exactly what to do, walk me through this, it would be amazing.


/dev/sda
  /dev/sda1 ntfs   104mb size 35mb used
  /dev/sda2 ntfs   104752mb size 38090mb used
  freespace        395248mb

thats how it all looks right now with only windows put on there.

---

### Post by Joe of loath on 2011-06-08
You'll want to create an EXT4 partition, and set the mountpoint to /. I'd say that 380gb is too much for Ubuntu, since you'll want to store your files where both Windows and Ubuntu can access them, I'd suggest creating another NTFS partition, of maybe 300gb, for movies, music, pictures etc.

You'll also want a 4gb partition formatted as swap.

---

### Post by nzjethro on 2011-06-08
I'm dual booting, with 100GB for Win, 100GB for 'buntu, and about 120GB for shared files.

Even then, I think 100GB for Ubuntu may be too big. Haha.

---

### Post by Rubi1200 on 2011-06-08
Hi and welcome to the forums kainu7 :)

This is an excellent site with instructions on dual-booting:
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by kainu7 on 2011-06-08
Yes I wasnt going to leave all 380 for linux =P I wanted most of it as shared for movies and music and such like you said. I was going to give ubuntu maybe 40gig of that. then i have my 4gig swap. 


so right now i need to make the following

4gig swap
40gig ext4 / 
336gig nsfs 

and then just install ubuntu onto the 40gig right??

---

### Post by Joe of loath on 2011-06-08
That sounds perfect.

I recommend putting both the ext4 and the swap into an extended partition, since you can only fit four primary partitions on the drive.

---

### Post by kainu7 on 2011-06-08
extended partition is that the "Logical" part right?

---

### Post by Joe of loath on 2011-06-08
I believe so, yes.

---

