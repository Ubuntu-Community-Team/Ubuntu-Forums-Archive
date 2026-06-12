---
title: "Switch to Ubuntu only"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by alch on 2008-07-03
I have a laptop that was (is) running vista. i installed ubuntu as an experiment a few days ago. i went with the install as an application/dual boot method. i have been very happy with the OS and I am just about ready to switch over permanently. Pretty much everything is working the same/better than vista imo.

Now is there a way I can make my current installation take over the rest of the hard drive? or do I have to start all over...

Thanks in advance.

---

### Post by SkonesMickLoud on 2008-07-03
It's quite simple actually:

First and most important, make sure you actually want to do this!!!  Once your windows partition is gone, it in incredibly difficult, if not impossible to get back.  Make sure you back up any files in Windows that you do not want to lose.

Now that you're sure you want to do this:

Boot into the LiveCD or GParted CD.  If you boot to the LiveCD, go to "System >> Admin >> Partition Editor/GParted".  Right click on your current Windows partition, select "delete", then right click on your Ubuntu partition and click on "Resize/Move or "Grow Partition".  Move the slider as far to the right as you can, click "Resize" (or something to that effect, I can't remember), then click Apply on the main screen.  Depending on the size of the partition, this could take some time.

When it's done, voila!  Larger Ubuntu partition.

Make sure you don't format over the swapspace.

[EDIT]  If you installed using wubi, then as far as I know, you will have to start over.  If this is the case, simply boot into the Ubuntu LiveCD and when it prompts you, tell it to use the entire disk.  If you want to try some manual partitioning (really, it's not as complex as it sounds) try this:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

IMO, installing with a separate /home is the way to go, as you can get away with ruining your Ubuntu install and then simply wiping your / partition without losing all of your files.

---

### Post by alch on 2008-07-03
Thanks! Sounds good.

I want to tweak a couple of little things and make sure I can get them working, then I think im ready. I already have everything backed up onto another machine so it shouldnt be a problem.

One of the things I was trying to do was get my blackberry to work as a tethered modem on ubuntu, but this might be the wrong forum.

---

### Post by SkonesMickLoud on 2008-07-03
> **alch said:**
> Thanks! Sounds good.

I want to tweak a couple of little things and make sure I can get them working, then I think im ready. I already have everything backed up onto another machine so it shouldnt be a problem.

One of the things I was trying to do was get my blackberry to work as a tethered modem on ubuntu, but this might be the wrong forum.

No problem!  Let us know how it goes if you would.

As for the blackberry, I haven't a clue, but I'm sure folks over here would be glad to help you out:

[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

---

### Post by AZinOH on 2008-07-03
> **SkonesMickLoud said:**
> It's quite simple actually:

First and most important, make sure you actually want to do this!!!  Once your windows partition is gone, it in incredibly difficult, if not impossible to get back.  Make sure you back up any files in Windows that you do not want to lose.

Now that you're sure you want to do this:

Boot into the LiveCD or GParted CD.  If you boot to the LiveCD, go to "System >> Admin >> Partition Editor/GParted".  Right click on your current Windows partition, select "delete", then right click on your Ubuntu partition and click on "Resize/Move or "Grow Partition".  Move the slider as far to the right as you can, click "Resize" (or something to that effect, I can't remember), then click Apply on the main screen.  Depending on the size of the partition, this could take some time.

When it's done, voila!  Larger Ubuntu partition.

Make sure you don't format over the swapspace.

[EDIT]  If you installed using wubi, then as far as I know, you will have to start over.  If this is the case, simply boot into the Ubuntu LiveCD and when it prompts you, tell it to use the entire disk.  If you want to try some manual partitioning (really, it's not as complex as it sounds) try this:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

IMO, installing with a separate /home is the way to go, as you can get away with ruining your Ubuntu install and then simply wiping your / partition without losing all of your files.

Can I use the live CD to increase the size of the Ubuntu partition, without deleting the Windows partition?

---

### Post by SkonesMickLoud on 2008-07-03
> **AZinOH said:**
> Can I use the live CD to increase the size of the Ubuntu partition, without deleting the Windows partition?

They only way this would be viable would be if your Ubuntu partition had unallocated space behind it.

---

### Post by Rplus9 on 2008-07-03
I did this recently, it will take a long time to do the re-partition.

I also encourage the separate /home partition, it's great to jump around OS's and still have all the important stuff waiting for you when you first boot up.

One thing I haven't figured out, is there a good way to partition and mount a drive to save the installed programs (wine, etc)?

---

