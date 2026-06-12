---
title: "When Partitioning during installation only shows up 2 options"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by D.Sync on 2008-05-31
Hi there, I am just a fresh new user for Linux OS System and I decided to choose Ubuntu after any other kernel system.

I had downloaded Ubuntu 8.04 LTS (couldnt' figure out what LTS means) and burn it onto a CD.

However, there's a problem when I tried to Install Ubuntu onto my Acer Aspire 5920G Laptop Computer. Whenever the installation reaches the partitioning option (step 4 I think), it only shows 2 option, which is [Guided Mode - Use this entire disk completely]&[Manual Setup]. I had found guides by googl'ing the internet and most guide stated there should be 3 options which one of them is friendly user which only requires user to drag the bar according to the user needs for the disc space for Ubuntu.

I had installed Ubuntu on my another desktop beforehand and it does shows up the 3 options aforementioned.

**Solution: You probably already have 4 primary partition. Just delete a partition, restart your computer, and the option for [Guided Mode - Resize partition] will occur the next time you install from Ubuntu LIVE CD! :)**

---

### Post by Sef on 2008-05-31
> I had downloaded Ubuntu 8.04 LTS (couldnt' figure out what LTS means) and burn it onto a CD.

LTS = Long Term Support.  For the desktop you have 3 years of support and 5 years on the server.  Normally for both, it is 18 months.

> I had installed Ubuntu on my another desktop beforehand and it does shows up the 3 options aforementioned.

Is this the same cd?  In any case, Run check disc for error. (Below the intall/boot option.)

---

### Post by Stefanie on 2008-05-31
i had the same problem, if you're using windows right now you have to boot into windows and make sure chkdsk runs when you reboot (in xp you have to right-click your c-drivein my computer, then select one of the tabs and click "check this drive for errors" or something like that).

---

### Post by D.Sync on 2008-05-31
> **Sef said:**
> LTS = Long Term Support.  For the desktop you have 3 years of support and 5 years on the server.  Normally for both, it is 18 months.



Is this the same cd?  In any case, Run check disc for error. (Below the intall/boot option.)

Ya, it's the same CD. So I need to run chkdsk for it to detect?

---

### Post by Stefanie on 2008-05-31
no, you need to run chkdsk to correct errors on your c-drive.&#12288;the ubuntu installer can't resize the partition when there are errors, you see.

---

### Post by D.Sync on 2008-05-31
I already run chkdsk and it found no problem at all. Just wonder how come it only shows up 2 options instead of 4 options when I installed it on my P4 3.0 GHZ desktop.

---

### Post by azizzle on 2008-05-31
I can't resize either my windows or my other ubuntu partition. I tried reinstalling ubuntu from an already dual boot. When the partition editor on the livecd stalled i restarted my computer. Now I can't resize either partition. I ran chkdsk on windows, but still I can't resize it. How do I check my ubuntu partition?

---

### Post by D.Sync on 2008-05-31
After trial and error I finally found the solution!

If you can't see the option for 'Guided Mode - Resize partition', then you probably already have 4 primary partition, hence Ubuntu cannot resize it.

To solve this problem, just delete a partition which you didn't want to use any more (should be >5GB since you might love Ubuntu), restart your computer, then run the installation from Ubuntu LIVE CD again. Then voila! The option does exist!

---

