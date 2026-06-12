---
title: "Lucid and RAID - fixed?"
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ed-koala on 2010-04-12
I have not seen this mentioned anywhere so I'll ask.

I had to install 9.10 on my system via the AMD 64 alternate install CD due to my fake(?) raid in my system.  I could not get it working even though the regular CD "sees" a 1TB drive instead of 2 500gb drives.

Anyhow, is this going to be the same situation with Lucid?  I'd love a simple install this time.  Using the alternate CD with Windows 7 (9.10) seems to lose windows boot info, and it isn't easy to recover. I hope RAID gets easier to set up soon.  I can't use my 2 drives as raid because it's too complex to install and then set up.

---

### Post by ronparent on 2010-04-12
I am currently experiencing the same problem with lucid from alpha 1 thru beta 2 and have yet been able to sucessfully in stal it on my prime machine. I can boot live CD with nodmraid, but I stand little chance of installing to a raid 0 unless that situation is remydied. Meanwhile, I guess I will have to sit on the sidelines.

---

### Post by nanog on 2010-04-12
you could turn off raid in you bios and install via software raid. there is little difference in speed.

---

### Post by ronparent on 2010-04-12
I appreciate your comment but I am trying to install dual boot with Win 7. Since the raid contains data I would like to access from both win and ubuntu I see little point in setting up a software raid.

---

### Post by ed-koala on 2010-04-13
Also, my BIOS has no setting whatsoever for RAID ... none, zero, zilch ... I've looked many times, so that isn't an option for me.

I sure hope the developers are working on RAID issues for the future, it's DESPERATELY needed.

---

### Post by Stason on 2010-04-13
Nope, it is not going to be easy folks, ever. It is "beyond developers capabilities and design features". Use the instructions here instead - it worked for me: [http://ubuntuforums.org/showpost.php?p=8643812&postcount=40](http://ubuntuforums.org/showpost.php?p=8643812&postcount=40)

P.S: Grub2 is still apparently no go either for most of the fake raids

---

### Post by ed-koala on 2010-04-13
I'll forgo Raid, it isn't vital to me.  Currently still wondering how to get my 9.10 and Windows 7 to dual boot.  Grub2 won't find Win 7, but that's a post in another section.

---

### Post by ronparent on 2010-04-13
Thank you very much Stason. I have bookmarked and will definitely try it. 

I have been fighting this problem in one form or another for about three years. I tired of it and skipped 9.10 so I never looked for that post!? Actually I tired of the gratuitous advise to use a software raid or 'real' hardware raid. I will stick with windows if oferred the alternative of abandoning it to be able to access data on raid drives.

---

