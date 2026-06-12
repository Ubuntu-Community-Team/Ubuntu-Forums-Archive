---
title: "Need help with swap and other upgrade problems"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by Omnios on 2007-12-30
I am having a problem with Ubuntu after a hardware swao.

 K the story so far. A while ago I bought my dad a used P4 and just got his old box. A while ago we both bought nearly exact except for hard drives.

 Anyways my dads P4 is in better shape and had front mounted usb's so I put all my P4s guts into that box. The only changes are I whent from 256m rat to 512 and replaced my old 40gig hard drive with a 80 gig that was in my dads tower.

 After a few problems I kind of got fstab working to the point of no errors but its taking very long to boot up. 

 My main problems now seem to be with swap as I noticed something weird in qtparted. I am blanking the old partitions ntfs part and an old lin part to make a doc, my documents partition. But first I have a swap problem with this drive. 

 In qtparted the swao is in two parts.

/dev/sdb3 extended 729.52
 |_ /dev/sdb5 linux swap 729.48

 Thr sbd5 is in the sdb3.

 I think this is causing problems and need to fix this. 

 Also now that I have 512m ram should I increase swap to 1G

 Also my ram is currently running at about 52% used by programs and 23% used by cach. Is this a but as with 256 it used all of the ram.

 From what I have seen so far the only problem seems to be with the new 80G drive which I will be reformating as soon as I fix the swap partition wich has some free space beside it.

 Also this is new territory for me and after trying to figure it out for about a day guess I will ask for help.

---

### Post by erfahren on 2007-12-30
> 
/dev/sdb3 extended 729.52
|_ /dev/sdb5 linux swap 729.48

that's normal. There's an unused area created by the extended partition (I can't explain it any better than that).

take a look at a screenshot of mine. The extended partition is ~20GB and then the other Linux partitions are created *out of it*.

---

### Post by Omnios on 2007-12-30
K got the partition problem solved and got my extra drive set up, have to do some  permition stuff with it. 

 Seem to have all the partition keys set up rioght.

 Im still having problems on boot as it seems to stand in one spot for a very long time. Is there a way to see boot text posts on os boot?

---

### Post by erfahren on 2007-12-30
if Gutsy is taking a long time to boot (but still boots eventually) could be the problem with the usplash resolution 

see:
[http://ubuntuforums.org/showpost.php?p=3741687&postcount=21](http://ubuntuforums.org/showpost.php?p=3741687&postcount=21)

---

