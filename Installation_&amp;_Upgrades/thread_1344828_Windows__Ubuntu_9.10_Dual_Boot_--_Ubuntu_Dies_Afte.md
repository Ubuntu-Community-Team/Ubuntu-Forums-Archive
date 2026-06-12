---
title: "Windows / Ubuntu 9.10 Dual Boot -- Ubuntu Dies After Windows Login"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by pRtkL xLr8r on 2009-12-03
Ok so for the past few days I've been trying to track this problem down and finally did, so maybe this will help someone else.

I installed Ubuntu 9.10 on a netbook that already had Windows XP.  Ubuntu runs fine, and then booting to windows from the grub menu works fine...

UNTIL

You boot Ubuntu from the grub menu -- black screen, blinking cursor!  You can fix this by going into the recovery mode for Ubuntu (which at least that worked, which was odd) and running update-grub.  Ubuntu will then load up just fine from the grub menu.

UNLESS

You boot Windows again -- then the same thing happens.

FINALLY 

Found out today after numerous searches the issue.  I found the answer [here]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941") -- I had heard dynamic disk partioning may be the cause (which I don't have) or virus software (which I removed).  I have a Compaq netbook -- HP product.  Turns out they have HP Recovery tools that will overwrite parts of the MBR.  The thing is, I uninstalled every single piece of their recovery software, sync software, etc, cuz I didn't want any of that crap.  I went into services, and lo-and -behold -- there was the hpqwmiex service running.  So I disabled it, did the update-grub thing again, logged into Windows then back into Ubuntu, and all is well!

Hopefully someone will see this...it was a huge headache, and since it's my first time using Ubuntu, it was a bit of a headache...I see on the thread I posted that grub 1 had none of these issues -- unfortunately, if you want ext4, you need grub2.

---

### Post by oldfred on 2009-12-03
Thank you for posting. I have seen several others with this problem and knew about the bug. Knowing exactly what service is causing it helps in solving boot issues. I will add a link to this post as a possible solution, if I happen across someone else with similar issues.

---

### Post by phillw on 2009-12-03
> **pRtkL xLr8r said:**
> Ok so for the past few days I've been trying to track this problem down and finally did, so maybe this will help someone else.

I installed Ubuntu 9.10 on a netbook that already had Windows XP.  Ubuntu runs fine, and then booting to windows from the grub menu works fine...

UNTIL

You boot Ubuntu from the grub menu -- black screen, blinking cursor!  You can fix this by going into the recovery mode for Ubuntu (which at least that worked, which was odd) and running update-grub.  Ubuntu will then load up just fine from the grub menu.

UNLESS

You boot Windows again -- then the same thing happens.

FINALLY 

Found out today after numerous searches the issue.  I found the answer [here]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941") -- I had heard dynamic disk partioning may be the cause (which I don't have) or virus software (which I removed).  I have a Compaq netbook -- HP product.  Turns out they have HP Recovery tools that will overwrite parts of the MBR.  The thing is, I uninstalled every single piece of their recovery software, sync software, etc, cuz I didn't want any of that crap.  I went into services, and lo-and -behold -- there was the hpqwmiex service running.  So I disabled it, did the update-grub thing again, logged into Windows then back into Ubuntu, and all is well!

Hopefully someone will see this...it was a huge headache, and since it's my first time using Ubuntu, it was a bit of a headache...I see on the thread I posted that grub 1 had none of these issues -- unfortunately, if you want ext4, you need grub2.

Hi,

Thanks for posting this information. What a nightmare !!  As the cry goes out - The more people who take the time to test an upcoming release on a 'spare' area / disk of their computer - the more mixes of computers & associated hardware can be checked out. Glad to see you got it sorted, and the dev's have got it noted, although, as noted in the bug-report - there's not too much they can do if Win, under Dell or HP is wandering around stamping bits into the MBR - I did like the comment >  I will take a look at services.msc and see if there's anything obvious like "Windows every-couple-of-weeks-bootsector-destroyer"!!A good sense of humour is always a welcome trait.

Regards,

Phill.

---

### Post by oldgeekster on 2009-12-03
> **oldfred said:**
> Thank you for posting. I have seen several others with this problem and knew about the bug. Knowing exactly what service is causing it helps in solving boot issues. I will add a link to this post as a possible solution, if I happen across someone else with similar issues.oldfred, I don't think this can be classified as a "bug" any longer when it is being caused by HP is bit-fiddling with the MBR?

---

### Post by phillw on 2009-12-03
> **oldgeekster said:**
> oldfred, I don't think this can be classified as a "bug" any longer when it is being caused by HP is bit-fiddling with the MBR?

It has a bug-report, classified as Confirmed - guess that makes it a bug.

If Grub2 is dying where Grub legacy worked - then it is something the Grub2 team need to investigate.

Phill.

---

### Post by darkod on 2009-12-03
I guess it is something in between. In my understanding grub1 needed less space on the MBR because it had other files using in /boot. If because of this or anything else, grub2 takes more space on the MBR and that HP tool slices part of the MBR, that wouldn't be entirely grub2 fault neither. HP tools have no business slicing the MBR right?
But hey, who is asking us.. :)

---

### Post by phillw on 2009-12-03
> **darkod said:**
> I guess it is something in between. In my understanding grub1 needed less space on the MBR because it had other files using in /boot. If because of this or anything else, grub2 takes more space on the MBR and that HP tool slices part of the MBR, that wouldn't be entirely grub2 fault neither. HP tools have no business slicing the MBR right?
But hey, who is asking us.. :)

Indeed, but as M$ get a bit more desperate, I guess we're going to see these 'security & recovery' more and more. Win XP, Vista Win7 et all are not totally to blame ... it's HP et all with their recovery areas & recovery s/ware. Otherwise, Grub2 wouldn't sit, side by side, with the M$ operating systems as it does.

The thing's they'll do to NOT ship a cd !!!! ;)

Phill.

---

