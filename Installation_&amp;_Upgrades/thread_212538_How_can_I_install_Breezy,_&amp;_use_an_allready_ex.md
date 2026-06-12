---
title: "How can I install Breezy, &amp; use an allready existant /home drive?"
date: 2006-07-10
forum: Installation &amp; Upgrades
---

### Post by handy on 2006-07-10
I have a separate /home drive partitioned solely for my data =  /dev/sda which I am using with a Dapper install.  

I want to be able to use the same /home drive, with a new Breezy install.

Breezy will be on it's own seperate drive.

It was not hard to do with Dapper, (once I worked it out!!).

It looks much harder in Breezy, I can't see away through? :confused: 

By the way, I am not dual booting, I use drive draws to exchange drives between boots.

Thanks for your help in advance.

---

### Post by aysiu on 2006-07-10
Just go through the installer and mount your root partition at **/** and your /home partition at **/home**.

For the /home partition be sure to **un**check the *reformat* box. Otherwise your data will be overwritten

---

### Post by handy on 2006-07-10
Thanks for your reply Aysiu.

I certainly can be a bit thick sometimes...

I didn't see how to do that with the Breezy installer?

It is much different than the Dapper one.

Any input is much appreciated?

---

### Post by aysiu on 2006-07-10
Wait--so you're downgrading to Breezy...?

---

### Post by handy on 2006-07-10
> **aysiu said:**
> Wait--so you're downgrading to Breezy...?

I have to run a Breezy drive because Guild Wars will not run on my Dapper system?  Something about an unrecognised graphics card (6800gt), which runs beautifuly under Breezy & Cedega.

I got a pile of seg faults in my Breezy drive, so I took the oportunity to set up /home on another drive.  Dapper is working with it fine.  But it looks really hard to do a Breezy install, with Breezy acknowledging the /home drive for what it is?

So I'm only running Breezy until I can get around the GW problem.  Transgaming are no help, there forums are useless & I don't like the atmosphere there either.  No one here has been able to crack the problem, so Breezy it is!

---

### Post by lordlollo on 2006-07-10
Probably I can't remember well the breezy installer, but it should ask you if you want to manually edit your partition table and so on... ;)

---

### Post by KalasMannen on 2006-07-10
As far as i know, the installer will ask if you want to edit partitiontables manually. Then it should be pretty easy to make it use your other disk as /home. Just make sure it doesn't format it!

---

### Post by handy on 2006-07-10
> **KalasMannen said:**
> As far as i know, the installer will ask if you want to edit partitiontables manually. Then it should be pretty easy to make it use your other disk as /home. Just make sure it doesn't format it!

Manually edit, yes, easy to make it use /home, no.

It's nothing like the Dapper installer, which I used yesterday to do the same thing.

---

### Post by aysiu on 2006-07-10
Just press Enter on the partition you want to see the options for.

If an option looks good to you, leave it alone. If it doesn't, press Enter on that option, and change it to what you like.

For example, if it says, "Yes, reformat," and you want it to say "No, do not reformat," just press **Enter** on "Yes, reformat," and it'll change.

Likewise, if it says *Mount Point: /media/hda2* and you want it to say *Mount Point /home*, just press **Enter** on *Mount Point: /media/hda2* and select */home* from the list.

When you're satisfied with how the screen looks, select **Done setting up partition** and press **Enter**.

---

### Post by handy on 2006-07-10
Thanks Aysiu, I'll give it a try as soon as I get rid of another problem (someone elses!).

I'll feedback here.

Thanks again. :KS

---

### Post by lordlollo on 2006-07-10
Anyway, assuming that your /home is not bigger than a TB, you should probably feel more confident with an old, beloved, physical backup! Then, try to follow the wave... ;)

---

### Post by handy on 2006-07-10
> **aysiu said:**
> Just press Enter on the partition you want to see the options for.

If an option looks good to you, leave it alone. If it doesn't, press Enter on that option, and change it to what you like.

For example, if it says, "Yes, reformat," and you want it to say "No, do not reformat," just press **Enter** on "Yes, reformat," and it'll change.

Likewise, if it says *Mount Point: /media/hda2* and you want it to say *Mount Point /home*, just press **Enter** on *Mount Point: /media/hda2* and select */home* from the list.

When you're satisfied with how the screen looks, select **Done setting up partition** and press **Enter**.

Thanks Aysiu, your information is spot on!  My Breezy installation is proceeding with all the partitions being recognises just the way I want them to be. :KS

Partitioning is such an important thing, so often fraught with dire consequences for valuable data & time if you get it wrong.

It is not obvious what to do with the Breezy installation at the partition management stage, nor is it with Dapper at the same stage.  I will see if the developers will put the small amount of instruction required to point users to the next hidden step, for future releases.

---

