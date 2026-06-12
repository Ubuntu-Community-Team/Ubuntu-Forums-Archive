---
title: "new to this need help installing ubuntu!"
date: 2008-06-15
forum: Installation &amp; Upgrades
---

### Post by thex707 on 2008-06-15
[SIZE="3"][FONT="Arial"]Ok hi! Well I am all new to this and hopefully I'll get good at this. Well anyways I obviously want to install ubuntu but I also would like to dual boot with XP. Well I go to the partition part of the installing but it only gives me three options. The guided - replacing xp altogether, the continuous one and manual. I go to manual and it gives me this:

 /dev/sda
  /dev/sda1    fat32       4GB   
  /dev/sda2    ntfs        33GB  --- unknown free space left
  Free Space               7MB

 well the ntfs one is the one that has xp in it. I want to partition that one but I just don't know how. It doesn't give me how much free I have left either (in xp it says 16.3GB). Oh yeah the FAT32 one is the recovery part for XP. I do not want to format it or anything and I have backed up my pics and stuff. how can one be able to parition the NTFS so I can get room for ubuntu and convert the allocated space necesary for it?  any help is greatly appreciated thanks!!![/FONT][/SIZE][SIZE="3"][/SIZE]

---

### Post by Partyboi2 on 2008-06-16
Boot the live cd and go to Partition Editor (System>Admin>Partition Editor) Once this is open use the resize feature. So highlight /dev/sda2 and right click and make sure it is unmounted. Then  click on the resize/move button and shrink it down to the size you want. Then restart the ubuntu installer and choose "manual" and create a /(root) partition and a swap (about x2 amount of onboard ram but probably not needing anymore then 2gig) then optionally a /home partition. So for and example if you were going to allocated 13 gig for ubuntu and had 512mb ram you could set it up something like this.
4gig /
8gig /home
1gig swap

---

### Post by thex707 on 2008-06-16
I went there and there was a problem. The NTFS parition was flagged and it said "boot" in the flag section. Also I tried to resize it but it only let me like 7MB of it!!!! Does it need to be reformatted if that is the last resort?

---

### Post by thex707 on 2008-06-17
I got it working!!! All I did was reading and found some thing and I did a Checkdisk from XP and it check it and it said like freedspace and I went back to the LiveCD parition thingy an I let me do it!! I am really excited!!! thanks for telling me how much I should allocate the memory!!

---

