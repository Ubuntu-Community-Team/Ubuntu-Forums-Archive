---
title: "xubuntu 6.10 livecd error"
date: 2006-11-28
forum: Installation &amp; Upgrades
---

### Post by lopio on 2006-11-28
hi, i tried to install xubuntu in 2 different pc (a new one and an old machine) 
but i obtain the same error.: at the end  of the installation, after having copied all files the install program fails to install grub.
I forced to install grub in diffrerent places bu nothing changed (and i can't report log message)
Is it a release bug?
Thanks

---

### Post by lhtown on 2006-11-29
It sounds to me like your CD might be bad.

I think there is an option on the CD itself to verify itself. I would try that before anything else.

Also, if you are using the same CD drive to install Xubuntu to both computers, it might be appear to work fine, but be giving you some errors.

By the way, Ubuntu and Kubuntu are easier to configure and get going than Xubuntu. I would recommend using one of them if you are trying to install and maintain it yourself.

---

### Post by garya on 2006-11-30
I downloaded the Xubuntu 6.10 live cd, and it freezes up my computer when I run it, so I downloaded it again and burned another CD.  I still can't get it to run properly--I don't get a toolbar at the top, so I can't try anything out.  I have an old Compaq Armada 7800, with a 266MHz processor and 224MB of RAM, so I need a stripped-down version of Ubuntu.  I have 6,06LTS, which seems to be working ok (for the most part), but I wanted to try the upgrade.  Could there be a bug?

---

### Post by lhtown on 2006-11-30
I haven't used XFCE in about six months or so, but I think the toolbar is still at the bottom of the screen by default.

Also, if your CD writer is flaky (and it sounds like it might be), you should verify the disk contents before you try to install it. You can still verify the CD after you installed it to see if that might have been part of the problem you are experiencing. 

If your install disk was corrupted by a flaky burn, all bets are off as to what you will get. If it was currupted, you might try burning another one on the slowest speed setting to see if that helps or try another brand of media. Some CD writers don't like certain brands of disks.

Also, you can use md5sum from the command line to verify the file that you downloaded. If it checks out with md5sum (you have to compare the number it gives you with the number on that ubuntu provides on the download server), it is fine and there is no need to try to download it again.

You should have enough ram to use the live CD, but with a computer that slow, personally, I would try the alternate install after trying to run the live CD.

---

### Post by garya on 2006-11-30
> **lhtown said:**
> I haven't used XFCE in about six months or so, but I think the toolbar is still at the bottom of the screen by default.


Forgive me--I didn't get the bar across the top of the screen where one can click on "applications" and get a pull-down menu.
> 
Also, if your CD writer is flaky (and it sounds like it might be), you should verify the disk contents before you try to install it. You can still verify the CD after you installed it to see if that might have been part of the problem you are experiencing. 

I did verify the disk.  Nothing wrong with my writer--I used my work computer, which is very nice.  At home, though, I live with a hand-me-down computer from my brother.
> 
You should have enough ram to use the live CD, but with a computer that slow, personally, I would try the alternate install after trying to run the live CD.

I think this may be the problem.  It looks like there's a bug in the recommended upgrade path, andI was hesitant to try apt-get.  I'll burn the alternate install CD if I go ahead.

---

