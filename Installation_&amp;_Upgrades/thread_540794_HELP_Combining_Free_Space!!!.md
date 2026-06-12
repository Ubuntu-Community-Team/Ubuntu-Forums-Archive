---
title: "HELP Combining Free Space!!!"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by fallenfantasyx on 2007-09-02
Hello,

Im kinda of in a bind, ive been playing with kubuntu linux on VMware with my xp install to learn how to compile source code and such,

Tonight i had to restart my computer and when xp went to load it crashed before the login screen and kept doing it, safe mode and last known config did not do anything.

im fed up with windows and its constant crashing and bugs, ive installed 3 times in the last 4 months because it just turned into garbage,

im a gamer, and im willing to take a hit on framerate to run Cedega 6.0 i dont carea anymore i just want to get rid of windows its so frustrating

anyway enough of my whining. my problem is when i run the kubuntu live cd and go to install when i get to partitions im a bit stuck on the issue not cause i dont know what im doing ive setup linux before but b/c of my ackward drive setup.

i have 2 drives and IDE and a SATA not that that matters but on my sda which is a 250gb SATA drive, i have the first 10gb for the windows install, the next 230 for Storage (my torrents videos music etc) and my last 10gb was for VMware to use...when i go to partition for kubuntu it will not let me erase my (2) 10gb partitions and combine them because the one is at the beginning of the drive the other is at the end (in between the 230gb of storage) i can not lose that 230gb of storage its my precious!, anyway once i delete the two 10gb partitions it will not let me create a swap THEN take the rest of the free space from both partitions and combine them into whats left (i make a 4gb swap, and i want the rest of that 10gb PLUS the other 10GB to make a 16gb / partition) is there a way to combine the rest of the OVERALL free space so i can just make the / partition...i get my new 320gb hard drive on tuesday and can backup my 230 then change it to ext3 if i have to but until then i need to use my computer and id like to get a headstart cause there aint a chance at fixing my windows install and i think 3 strikes is enough...

---

### Post by logos34 on 2007-09-02
I'd resize those partitions using the latest [Gparted Live CD.]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828")

Delete the two 10 GB partitions.

Expand the big storage partition into the unallocated space at the end of the disk by dragging the slider to the right.  (this should take just sec to complete)

Then click on the storage partition again to shrink from the LEFT. (this takes a lot longer....it has to copy the data over).  

Create your new ext3 and swap partitions in the newly enlarged free space.  Or simply begin the ubuntu installation and do the rest frm there.

EDIT:  and 4 GB is overkill for swap.  1GB should be plenty (for the average user).

---

### Post by fallenfantasyx on 2007-09-02
since im kinda stuck using live cd right now (its the only way i can run any OS, ty linux for using live) can i use Qpart while running just the live on ram, it sees my partitions when i load it

---

### Post by dmitriyp13 on 2007-09-02
Another thing you can do is have several mount points.  What I mean is this: mount your 10GB partition to "/" and your 6GB partition to something else, perhaps "/opt".

---

### Post by logos34 on 2007-09-02
> **fallenfantasyx said:**
> since im kinda stuck using live cd right now (its the only way i can run any OS, ty linux for using live) can i use Qpart while running just the live on ram, it sees my partitions when i load it

then just use the gparted on the ubuntu live cd (it's an older version but may work just as well)

in terminal:

sudo gparted

the reason I suggested the Gparted live cd is because someone said the older versions can't shrink/expand partitions on the left side.  hopefully that's wrong or I misread

EDIT: you could do like dmitriyp13 above suggests and make more than one partition...Maybe make a 9GB root and 1 GB swap in the 10GB space at the front of the disk and then a separate ext3 /home in the 10 gigs at the end.  Then again, maybe you prefer not to have them spread apart like that

---

